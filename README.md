### vibora
---
https://github.com/vibora-io/vibora

https://vibora.io/

```py
// tests/router/strategies.py

class RedirectStrategyTestCase(TestSuite):
  
  def setUp(self):
    self.app = Vibora(router_strategy=RouterStrategy.REDIRECT)
  
  async def test_missing_slash_expects_redirect(self):
    @self.app.route('/asd', methods=['GET'])
    async def home():
      return Response(b'123')
    
    client = self.app.test_client(follow_redirects=False)
    self.asssertEqual((await client.request('/asd/')).status_code, 301)
  
  async def test_missing_slash_with_default_post_route_expects_not_found(self):
    @self.app.route('/asd', methods=['POST'])
    async def home():
      return Response(b'123')
      
    client = self.app.test_client()
    self.assertEqual((await client.request('/asd/')).status_code, 404)
  
  async def test_wrong_method_expects_405_response(self):
  
  async def test_additional_slash_expects_redirected(self):
    @self.app.route('/asd/', methods=['GET'])
    async def home():
      return Response(b'')
      
    client = self.app.test_client(follow_redirects=False)
    response = await client.request('/asd', method='GET')
    self.assertEqual(response.status_code, 301)
    self.assertEqual('/asd/', response.headers['location'])
  
class StrictStrategyTestCase(TestSuite):
  
  def setUp(self):
    self.app = Vibora(router_strategy=RouterStrategy.STRICT)
  
  async def test_simple_get_router_expects_found(self):
  
  async def test_simple_get_route_expects_404(self):
  

class CloneStrategyTestCase(TestSuite):


```

```
```

```
```


