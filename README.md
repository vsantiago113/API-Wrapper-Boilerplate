# APIClientBoilerplate

Requirements for Testing
https://github.com/vsantiago113/RESTful-API-Boilerplate

---

### Import and instantiate the class
```python
from api.TestAPIClient import Client

client = Client(verify=False, warnings=False, api_version='v1')
```

### Connect and Disconnect
```python
from api.TestAPIClient import Client

client = Client(verify=False, warnings=False, api_version='v1')

client.connect(url='http://127.0.0.1:5000', username='admin', password='Admin123')

client.disconnect()
```

### HTTP GET all records
```python
from api.TestAPIClient import Client
import json

client = Client(verify=False, warnings=False, api_version='v1')

client.connect(url='http://127.0.0.1:5000', username='admin', password='Admin123')

response = client.get(method='routers', PageSize=10, Offset=0)
if response.status_code in [200, 202, 204]:
    print(json.dumps(response.json(), indent=4))
else:
    print(response.status_code, response.reason)

client.disconnect()
```

### HTTP GET a single record
```python
from api.TestAPIClient import Client
import json

client = Client(verify=False, warnings=False, api_version='v1')

client.connect(url='http://127.0.0.1:5000', username='admin', password='Admin123')

response = client.get(method='routers/123456')
if response.status_code in [200, 202, 204]:
    print(json.dumps(response.json(), indent=4))
else:
    print(response.status_code, response.reason)

client.disconnect()
```

### HTTP POST
```python
from api.TestAPIClient import Client
import json

client = Client(verify=False, warnings=False, api_version='v1')

client.connect(url='http://127.0.0.1:5000', username='admin', password='Admin123')

response = client.post(method='routers', data={'name': 'RT99', 'ip': '192.168.1.199'})
if response.status_code in [200, 202, 204]:
    print(json.dumps(response.json(), indent=4))
else:
    print(response.status_code, response.reason)

client.disconnect()
```

### HTTP PUT
```python
from api.TestAPIClient import Client
import json

client = Client(verify=False, warnings=False, api_version='v1')

client.connect(url='http://127.0.0.1:5000', username='admin', password='Admin123')

response = client.put(method='routers/123456', data={'name': 'RT300', 'ip': '192.168.1.230'})
if response.status_code in [200, 202, 204]:
    print(json.dumps(response.json(), indent=4))
else:
    print(response.status_code, response.reason)

client.disconnect()
```

### HTTP DELETE
```python
from api.TestAPIClient import Client
import json

client = Client(verify=False, warnings=False, api_version='v1')

client.connect(url='http://127.0.0.1:5000', username='admin', password='Admin123')

response = client.delete(method=f'routers/123456')
if response.status_code in [200, 202, 204]:
    print(json.dumps(response.json(), indent=4))
else:
    print(response.status_code, response.reason)

client.disconnect()
```

### How to use Dynamic Methods

#### HTTP GET all records
```python
from api.TestAPIClient import Client
import json

client = Client(verify=False, warnings=False, api_version='v1')

client.connect(url='http://127.0.0.1:5000', username='admin', password='Admin123')

response = client.get_routers(PageSize=10, Offset=0)
if response.status_code in [200, 202, 204]:
    print(json.dumps(response.json(), indent=4))
else:
    print(response.status_code, response.reason)

client.disconnect()
```

#### HTTP GET a single record
```python
from api.TestAPIClient import Client
import json

client = Client(verify=False, warnings=False, api_version='v1')

client.connect(url='http://127.0.0.1:5000', username='admin', password='Admin123')

response = client.get_routers_x('123456', placeholder='x', split_method='_')
if response.status_code in [200, 202, 204]:
    print(json.dumps(response.json(), indent=4))
else:
    print(response.status_code, response.reason)

client.disconnect()
```
