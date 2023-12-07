
```
# Request:
GET /artists

# Expected response (200 OK)
Pixies, ABBA, Taylor Swift, Nina Simone
```

## 1. Design the Route Signature

_Include the HTTP method, the path, and any query or body parameters._
```

# Add album route
POST /albums
  title: string
  release_year: number (str)
  artist_id: number (str)

GET /albums

GET /artists




# EXAMPLE

# Home route
GET /home

# Waving route
GET /wave?name=<string>

# Submit message route
POST /submit
  name: string
  message: string
```

## 2. Create Examples as Tests

_Go through each route and write down one or more example responses._

_Remember to try out different parameter values._

_Include the status code and the response body._

```python
# GET /artists
#  Expected response (200 OK):
"""
Pixies, ABBA, Taylor Swift, Nina Simone
"""

# POST /albums
#  Parameters:
#    title: Voyage
#    release year: 2022
#    artist id: 2
#  Expected response (200 OK):
"""
None
"""

# GET /albums
#  Expected response (200 OK):
"""
A list of albums
"""

# GET /wave?name=Leo
#  Expected response (200 OK):
"""
I am waving at Leo
"""

# GET /wave
#  Expected response (200 OK):
"""
I am waving at no one!
"""

# POST /submit
#  Parameters:
#    name: Leo
#    message: Hello world
#  Expected response (200 OK):
"""
Thanks Leo, you sent this message: "Hello world"
"""

# POST /submit
#  Parameters: none
#  Expected response (400 Bad Request):
"""
Please provide a name and a message
"""
```

## 3. Test-drive the Route

_After each test you write, follow the test-driving process of red, green, refactor to implement the behaviour._

Here's an example for you to start with:

```python
"""
GET /artists
  Expected response (200 OK):
  Pixies, ABBA, Taylor Swift, Nina Simone
"""
def test_get_artists(web_client):
  response = web_client.get('/artists')
  assert response.status_code == 200
  assert response.data.decode('utf-8') == 'Pixies, ABBA, Taylor Swift, Nina Simone'


"""
GET /home
  Expected response (200 OK):
  "This is my home page!"
"""
def test_get_home(web_client):
    response = web_client.get('/home')
    assert response.status_code == 200
    assert response.data.decode('utf-8') == 'This is my home page!'

"""
POST /submit
  Parameters:
    name: Leo
    message: Hello world
  Expected response (200 OK):
  "Thanks Leo, you sent this message: "Hello world""
"""
def test_post_submit(web_client):
    response = web_client.post('/submit', data={'name': 'Leo', 'message': 'Hello world'})
    assert response.status_code == 200
    assert response.data.decode('utf-8') == 'Thanks Leo, you sent this message: "Hello world"'

  
"""
POST /albums
  Parameters:
    title: Voyage
    release year: 2022
    artist id: 2
  Expected response (200 OK):
  (No content)
"""
def test_post_album(web_client):
    response = web_client.post('/albums', data={'title': 'Voyage', 'release year': '2022', 'artist id': '2'})
    assert response.status_code == 200
    
```


<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fweb-applications-in-python&prefill_File=resources%2Fplain_route_recipe_template.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fweb-applications-in-python&prefill_File=resources%2Fplain_route_recipe_template.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fweb-applications-in-python&prefill_File=resources%2Fplain_route_recipe_template.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fweb-applications-in-python&prefill_File=resources%2Fplain_route_recipe_template.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fweb-applications-in-python&prefill_File=resources%2Fplain_route_recipe_template.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->