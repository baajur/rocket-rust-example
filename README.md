# rocket-rust-example
An example of rust with rocket with a pinch of clean architecture

### Considerations
Tested in rustc 1.46.0-nightly

### Prerequisites

to run this project you need:
* Docker and docker-compose

### Run with docker

```bash
docker-compose up
```

### Run tests

#### Unit Tests

```console
cargo test --lib
```

#### Integration Tests

With docker after run tests you probably need to stop the db container

```console
docker-compose -f docker-compose-integration.yaml up
```

to run with cargo take in mind a db

 ```console
cargo test --test integration -- --test-threads=1
 ```

## Curl Quickly Functional Tests

### Create Bikes

`POST http://localhost:8000/bike`

**Auth required** : NO

**Response** POST Example

```json
{
  "description": "awful bike 3",
  "id": 8,
  "model": "Shimano 3"
}
```

**Example**

```console
curl --request POST \
  --url http://localhost:8000/bike \
  --header 'content-type: application/json' \
  --data '{
	"description": "awful bike 3",
	"model": "Shimano 3"
}
```

### Get Bikes

`GET http://localhost:8000/bikes`

**Auth required** : NO

**Response** GET Example

```json
[
  {
    "description": "awful bikes",
    "id": 1,
    "model": "Shimano"
  },
  {
    "description": "Awesome bike 1",
    "id": 2,
    "model": "Shimano 1"
  }
]
```

**Example**

```console
curl --request GET \
  --url http://localhost:8000/bikes
```

### Update Bikes

`PUT http://localhost:8000/bike/1`

**Auth required** : NO

**Response** PUT Example

```json
{
  "id": 7,
  "description": "awful bikes",
  "model": "Shimanowww"
}
```

**Example**

```console
curl --request PUT \
  --url http://localhost:8000/bike/1 \
  --header 'content-type: application/json' \
  --data '{
	"description": "awful bikes",
	"model": "Shimanow"
	
}
```

### Delete Bikes

`DELETE http://localhost:8000/bike/1`

**Auth required** : NO

**Response** DELETE Example

```json
{
  "status": "ok"
}
```

**Example**

```console
curl --request DELETE \
  --url http://localhost:8000/bike/1
```
