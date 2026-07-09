# web_connect2 · WalletConnect Verify 测试桩 (Case 2 · invalid)

这是 **invalid** 用例的部署站点，用于复现 WalletConnect Verify 的 `verifyResult = "invalid"`。

> 部署后 origin：`https://rayccc-ai.github.io/web_connect2`

## 这个站点对应哪个 tag

| 项 | 值 |
|---|---|
| 预期 verifyResult | **invalid** |
| 占位 projectId（需替换） | `PUT_INVALID_PROJECT_ID` |
| Dashboard allowlist 应配 | 与部署域名**故意不一致**的域名，例如 `https://declared.example.com` |
| 触发条件 | 请求真实 origin（`.../web_connect2`）与该 projectId 登记的 allowlist 域名不匹配，且未被标记 |

> 关键：让 allowlist 里登记的域名 ≠ 实际部署 origin，verify server 比对失败 → invalid。

## 开启 GitHub Pages（让站点上线）

1. 打开 https://github.com/rayccc-ai/web_connect2/settings/pages
2. **Source** 选 `Deploy from a branch`
3. **Branch** 选 `main` / `(root)` / `Save`
4. 等约 1 分钟，访问 https://rayccc-ai.github.io/web_connect2

## 替换为真实 projectId

```bash
cd <源项目 wallet-connect>
VITE_PID_INVALID=<你的真实projectId> VITE_GH_USER=rayccc-ai npm run build
cp -R dist/. <本仓库路径>/
git add -A && git commit -m "inject real projectId for invalid case" && git push
```

## 四种 tag 的完整说明

见源仓库 README。映射：`isScam==true → scam`，否则 `validation → valid/invalid/unknown`。
