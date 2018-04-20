# mcrouter

Run the container

```
docker run \
   --name mcrouter \
   --restart=always \
   -p 30000:30000 \
   -d \
   -v $(pwd)/mcrouter.conf:/etc/mcrouter.conf \
   --log-opt "max-size=100m" \
   jsecchiero/mcrouter
```

Mcrouter config example, put memcache servers here
```
{
  "pools": {
    "A": {
      "servers": [  "10.2.0.1:11211" ,  "10.2.0.2:11211" ]
    }
  },
  "route": {
    "type": "OperationSelectorRoute",
    "operation_policies": {
      "add": "AllFastestRoute|Pool|A",
      "delete": "AllFastestRoute|Pool|A",
      "get": "MissFailoverRoute|Pool|A",
      "set": "AllFastestRoute|Pool|A"
    }
  }
}
```
