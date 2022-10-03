---
id: rf7ard545adh8hhng23zob3
title: 'Papers, Please'
desc: ''
updated: 1664741509475
created: 1663852200000
tags:
  - python
  - 3-kyu
  - codewars
  - answer
---

### Python

```py
import re
from datetime import datetime

class Inspector:
    def __init__(self):
        self.allowed_countries = []
        self.requirements = []
        self.document_expiration_date = datetime(year=1982, month=11, day=22)
        self.criminal = ""
        self.current_entrant_info = {}


    def receive_bulletin(self, bulletin):
        # Update the allowed countries list with new countries
        allowed_countries = self.getRegex("Allow citizens of (.*)", bulletin)
        self.allowed_countries.extend(re.split(", ", allowed_countries))

        # Update the allowed countries list by removing denied countries
        denied_countries = self.getRegex("Deny citizens of (.*)", bulletin)
        self.allowed_countries = list(
          filter(lambda x: x not in denied_countries, self.allowed_countries)
        )

        # Update the list of requirements
        new_requirements = re.findall("(.*)(?<!no longer) require (.*)", bulletin)
        self.requirements.extend(self.createRequirementList(new_requirements))
        remove_requirements = re.findall("(.*) no longer require (.*)", bulletin)
        self.requirements = list(
          filter(
            lambda x: x not in self.createRequirementList(remove_requirements),
            self.requirements
          )
        )

        # Updates the criminal of the day
        criminal = self.getRegex("Wanted by the State: (.*)", bulletin)
        if criminal != "":
            names = criminal.split(" ")
            criminal = names[1] + ", " + names[0]
        self.criminal = criminal


    def inspect(self, documents):
        ##
        # Create objects out of the data from the available documents
        ##
        vaccination_info = documents.get("certificate_of_vaccination", "")
        vaccination_card = self.getDocumentData(vaccination_info)

        passport_info = documents.get("passport", "")
        passport = self.getDocumentData(passport_info)

        access_permit_info = documents.get("access_permit", "")
        access_permit = self.getDocumentData(access_permit_info)

        grant_of_asylum_info = documents.get("grant_of_asylum", "")
        grant_of_asylum = self.getDocumentData(grant_of_asylum_info)

        diplomatic_info = documents.get("diplomatic_authorization", "")
        diplomatic_authorization = self.getDocumentData(diplomatic_info)

        work_pass_info = documents.get("work_pass", "")
        work_pass = self.getDocumentData(work_pass_info)

        id_card_info = documents.get("ID_card", "")
        id_card = self.getDocumentData(id_card_info)

        ##
        # Add entrant information for use across functions
        ##
        self.current_entrant_info["vaccination_card"] = vaccination_card
        self.current_entrant_info["passport"] = passport
        self.current_entrant_info["grant_of_asylum"] = grant_of_asylum
        self.current_entrant_info["access_permit"] = access_permit
        self.current_entrant_info["diplomatic_authorization"] = diplomatic_authorization
        self.current_entrant_info["work_pass"] = work_pass
        self.current_entrant_info["ID_card"] = id_card

        ##
        # Entrant is detained
        ##
        if (
          (passport and self.criminal == passport["name"]) or
          (access_permit and self.criminal == access_permit["name"]) or
          (grant_of_asylum and self.criminal == grant_of_asylum["name"])
        ):
            return "Detainment: Entrant is a wanted criminal."

        id_list = self.getDocumentValues("id")
        if not all(x == id_list[0] for x in id_list):
            return "Detainment: ID number mismatch."

        nation_list = self.getDocumentValues("nation")
        nation = nation_list[0] if len(nation_list) else ""
        if not all(x == nation_list[0] for x in nation_list):
            return "Detainment: nationality mismatch."

        dob_list = self.getDocumentValues("dob")
        if not all(x == dob_list[0] for x in dob_list):
            return "Detainment: date of birth mismatch."

        name_list = self.getDocumentValues("name")
        if not all(x == name_list[0] for x in name_list):
            return "Detainment: name mismatch."

        ##
        # Entrant is denied for an invalid document
        ##
        diplomatic_nations = diplomatic_authorization.get("access")
        if diplomatic_nations and "Arstotzka" not in diplomatic_nations:
            return "Entry denied: invalid diplomatic authorization."

        ##
        # Entrant is denied from the country for an expired document
        ##
        if passport.get("expiration", datetime.now()) < self.document_expiration_date:
            return "Entry denied: passport expired."
        elif grant_of_asylum.get("expiration", datetime.now()) < self.document_expiration_date:
            return "Entry denied: grant of asylum expired."
        elif access_permit.get("expiration", datetime.now()) < self.document_expiration_date:
            return "Entry denied: access permit expired."

        ##
        # Entrant is a member of a denied country
        ##
        if len(nation) and nation not in self.allowed_countries:
            return "Entry denied: citizen of banned nation."

        ##
        # Assign the entrant groups based on their provided documentation
        ##
        groups = ["Entrants"]
        if nation == "Arstotzka":
            groups.append("Citizens of Arstotzka")
        else:
            groups.append("Foreigners")
            if len(nation): groups.append("Citizens of " + nation)
        if access_permit.get("purpose") == "WORK":
            groups.append("Workers")

        ##
        # Entrant is denied from the country for not meeting bulletin requirements
        ##
        for requirement in self.requirements:
            if requirement[0] in groups:
                requirement_met = self.checkForRequirement(requirement[1])
                if requirement_met is not True:
                    return "Entry denied: " + requirement_met

        # Entrant is allowed into the country
        if (nation == "Arstotzka"):
            return "Glory to Arstotzka."
        else:
            return "Cause no trouble."


    def getDocumentValues(self, key):
        values = []
        values.append(self.current_entrant_info["vaccination_card"].get(key))
        values.append(self.current_entrant_info["passport"].get(key))
        values.append(self.current_entrant_info["grant_of_asylum"].get(key))
        values.append(self.current_entrant_info["access_permit"].get(key))
        values.append(self.current_entrant_info["diplomatic_authorization"].get(key))
        values.append(self.current_entrant_info["work_pass"].get(key))
        values.append(self.current_entrant_info["ID_card"].get(key))
        return list(filter(lambda x: x is not None, values))


    def createRequirementList(self, requirement_list):
        for requirement in requirement_list:
            citizenship_requirement = self.getRegex("Citizens of (.*)", requirement[0])
            if citizenship_requirement:
                requirement_list.remove(requirement)
                countries = requirement[0].split(", ")
                requirement_list.extend(list(map(
                  lambda x: ("Citizens of " + x if not re.search("Citizens of ", x) else x, requirement[1]),
                  countries
                )))

        return requirement_list


    def checkForRequirement(self, requirement):
        if "vaccination" in requirement:
            vaccination_card = self.current_entrant_info["vaccination_card"]
            if not vaccination_card:
                return "missing required certificate of vaccination."
            vaccine = re.sub(" vaccination", "", requirement)
            if not vaccination_card or not re.search(vaccine, vaccination_card["vaccines"]):
                return "missing required vaccination."
        elif "passport" in requirement:
            if not self.current_entrant_info["passport"]:
                return "missing required passport."
        elif "access permit" in requirement:
            if (
              not self.current_entrant_info["access_permit"] and
              not self.current_entrant_info["grant_of_asylum"] and
              not self.current_entrant_info["diplomatic_authorization"]
            ):
                return "missing required access permit."
        elif "work pass" in requirement:
            if not self.current_entrant_info["work_pass"]:
                return "missing required work pass."
        elif "ID card" in requirement:
            if not self.current_entrant_info["ID_card"]:
                return "missing required ID card."

        return True


    def getDocumentData(self, doc):
        docData = {}
        for line in doc.splitlines():
            if "DOB: " in line:
                dob = self.getRegex("DOB: (.*)", doc)
                dob_parts = [int(x) for x in re.split("\.", dob)]
                docData["dob"] = datetime(year=dob_parts[0], month=dob_parts[1], day=dob_parts[2])
            elif "EXP: " in line:
                expiration = self.getRegex("EXP: (.*)", doc)
                expiration_parts = [int(x) for x in re.split("\.", expiration)]
                docData["expiration"] = datetime(year=expiration_parts[0], month=expiration_parts[1], day=expiration_parts[2])
            else:
                key, value = line.split(": ")
                key = re.sub("#", "", key.lower())
                docData[key] = value

        return docData


    def getRegex(_self, regex, data):
        regex = re.search(regex, data)
        return regex.group(1) if regex else ""
```
