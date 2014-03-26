# OvhApi

Python module to manage Ovh's API

## Examples

To send an hello world

```python
from ovhapi import Api, OVH_API_EU

ovh_app_key = XXXXXXXXXXXXXXXXXXXXX
ovh_secret_key = XXXXXXXXXXXXXXXXXX
ovh_consumer_key = XXXXXXXXXXXXXXXX

api = Api(root=OVH_API_EU,
          applicationKey=ovh_app_key,
          applicationSecret=ovh_secret_key,
          consumerKey=ovh_consumer_key
          )

service = api.get('/sms').json()

senders = api.get('/sms/%s/senders' % service)

phone = '+33601020304'

sms = 'helloworld'

try:
    self.api.post(
        '/sms/%s/jobs' % service,
        content={
            'sender': senders[0],
            'message': sms,
            'receivers': [phone],
            'noStopClause': True
        }
    )
except ConnectionError:
    print('Connection error')
```
