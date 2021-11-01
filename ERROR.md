高版本 node 报错

```
/data/wwwroot/homeplan/homeplan-xp/node_modules/gitbook-cli/node_modules/npm/node_modules/graceful-fs/polyfills.js:287
      if (cb) cb.apply(this, arguments)

TypeError: cb.apply is not a function
    at /data/wwwroot/homeplan/homeplan-xp/node_modules/gitbook-cli/node_modules/npm/node_modules/graceful-fs/polyfills.js:287:18
    at FSReqCallback.oncomplete (node:fs:199:5)
```

处理方案

vim xxx/polyfills.js

62行

```
  //fs.stat = statFix(fs.stat)
  //fs.fstat = statFix(fs.fstat)
  //fs.lstat = statFix(fs.lstat)
```

修改好执行

```
gitbook install
```

然后又会报一次，上次的地址是仓库依赖包，这次是全局的依赖包。

```
/usr/local/lib/node_modules/gitbook-cli/node_modules/npm/node_modules/graceful-fs/polyfills.js:287
      if (cb) cb.apply(this, arguments)
                 ^

TypeError: cb.apply is not a function
    at /usr/local/lib/node_modules/gitbook-cli/node_modules/npm/node_modules/graceful-fs/polyfills.js:287:18
    at FSReqCallback.oncomplete (node:fs:199:5)
```

同样的编辑 polyfills.js ，再执行 gitbook install 即可。
