#### 解决方法 vite.config.ts 下 增加配置

```js
export default defineConfig({
    plugins: [vue()],
    server: {
        watch: {
            usePolling: true
        }
    }
})
```

