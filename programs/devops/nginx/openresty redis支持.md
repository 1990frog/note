[TOC]

/openresty/lualib/resty/redis.lua

openresty帮我们封装完了整个redis的开发库

# 编写lua脚本
redis.lua
```lua
local args = ngx.req.get_uri_args()
local id = args["id"]
local redis = require "resty.redis"
local cache = redis:new()
local ok,err = cache:connect("ip",port)
local item_model = cache:get("item_"..id)
if item_model == ngx.null or item_model == nil then
    local resp = ngx.location.capture("/item/get?id="..id)
    item_model = resp.body
end

ngx.sql(item_model)
```
vim nginx.conf
```
location /luaitem/get{
    default_type "application/json";
    content_by_lua_file ../lua/redis.lua;
}
```