# web_connect2 · Case 2 · invalid

| 项 | 值 |
|---|---|
| 预期 verifyResult | **invalid** |
| WalletConnect projectId | （在 Vercel 环境变量 `VITE_PID_INVALID` 配真实值） |
| Dashboard allowlist 应配 | 一个与当前部署域名**故意不一致**的域名 |

## Vercel 环境变量（仅这一个）

```
VITE_PID_INVALID = <你的 invalid 用例 projectId>
```

> 让 allowlist 登记域名 ≠ 实际部署 origin → verify 比对失败 → invalid。
