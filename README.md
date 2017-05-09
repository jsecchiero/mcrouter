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
