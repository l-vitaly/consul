Go Consul Client Wrapper
========================

# API 

### GetServices(service string, tag string) ([]*consulapi.ServiceEntry, *consulapi.QueryMeta, error) 

get a services from consul

### GetFirstService(service string, tag string) (*consulapi.ServiceEntry, *consulapi.QueryMeta, error)

get a first service from consul

### RegisterService(name string, addr string, tags ...string) error 

register a service with local agent

### DeRegisterService(string) error

de-register a service with local agent

### Get(key string) (*consulapi.KVPair, *consulapi.QueryMeta, error)

get KVPair

### WatchGet(key string) chan *consulapi.KVPair

watch create/update KVPair 

### GetStr(key string) (string, error)

get string value

### GetInt(key string) (int, error)

get int value

### Put(key string, value string) (*consulapi.WriteMeta, error)

put KVPair

### LoadStruct(parent string, i interface{}) error

Load key/value to structure, basic usage:

``` golang
var s struct {
  Name string `consul:"default:Rob Pike"` // set default value if not exists key
  Size int    `consul:"default:100"`
  Url  string `consul:"name:u;default:http://localhost"` // different key name is "n"
  Other struct { // nested keys
    Name1 string `consul:"default:no"`
  }
}
```
