# Battle Mage 法律页面发布包

该目录包含《Battle Mage》的公开隐私政策和用户协议，可直接上传到静态网站托管服务。

## 文件对应关系

| 文件 | 用途 | 建议公开链接 |
|---|---|---|
| `privacy-policy.html` | 隐私政策，供 Google Play Console 的“隐私权政策”字段使用 | `https://你的域名/privacy-policy.html` |
| `terms-of-service.html` | 用户协议，可放在商店页、官网或开发者网站 | `https://你的域名/terms-of-service.html` |
| `index.html` | 两份文件的公开入口页 | `https://你的域名/` |
| `styles.css` | 页面样式，必须和 HTML 文件一起上传 | 无需单独分享 |

## 发布前必须确认

1. **开发者联系邮箱**：Google Play 商品页必须填写可用的支持邮箱。隐私政策中的删除请求、权利请求和用户协议中的联系说明都以该邮箱为准。
2. **运营者名称**：页面目前使用 Unity 工程中的 `companyName`：`SPIELPHANTOMLIMITED`。如果 Google Play 的实际发布主体不同，请统一替换。
3. **付费功能**：当前工程未接入应用内购买 SDK，用户协议按“当前未提供内购”描述；如果未来接入 Google Play Billing，请更新“虚拟物品与付费”部分。
4. **广告和分析 SDK**：当前 `AdFeatureConfig.AdsEnabled = false`，且未发现广告、独立分析或崩溃上报 SDK。隐私政策按该状态描述；接入 Firebase、Google Mobile Ads、AppsFlyer、Adjust、Unity Analytics 等后必须更新页面并重新评估数据安全表单。
5. **儿童受众**：如果 Google Play 目标受众包含儿童，或游戏被标记为面向儿童，请重新审核隐私政策中的未成年人部分，并按要求处理家长同意和广告/数据收集限制。
6. **适用法律**：用户协议目前的争议条款采用通用写法。正式发布前，建议由法务根据实际运营主体、注册地、目标市场和退款政策确认适用法律与管辖条款。

## 方案一：GitHub Pages（免费、适合长期公开链接）

1. 在 GitHub 创建一个 **Public** 仓库，例如 `battle-mage-legal`。
2. 将本目录内的 `index.html`、`privacy-policy.html`、`terms-of-service.html`、`styles.css` 和 `.nojekyll` 上传到仓库根目录。
3. 打开仓库的 `Settings` → `Pages`。
4. 在 `Build and deployment` 中选择 `Deploy from a branch`。
5. 分支选择 `main`，目录选择 `/ (root)`，保存。
6. 等待约 1 至 5 分钟后访问：

```text
https://<你的 GitHub 用户名>.github.io/battle-mage-legal/privacy-policy.html
https://<你的 GitHub 用户名>.github.io/battle-mage-legal/terms-of-service.html
```

> GitHub Pages 的公开页面不需要访客登录。请确认仓库为公开仓库，且不要启用会阻止直接访问的访问控制。

## 方案二：Cloudflare Pages

1. 登录 Cloudflare 控制台，进入 `Workers & Pages`。
2. 选择 `Create` → `Pages` → `Upload assets`。
3. 将 `legal-site` 目录内的文件整体上传，或将本目录压缩后上传。
4. 完成部署后，Cloudflare 会提供一个 `*.pages.dev` 公开地址。
5. 在 Cloudflare 中将 `privacy-policy.html` 和 `terms-of-service.html` 作为两个独立链接使用。
6. 如有自己的域名，可在 Pages 项目中绑定自定义域名。

## 方案三：Netlify Drop

1. 打开 Netlify 的 `Deploy manually` 或 `Netlify Drop` 页面。
2. 将整个 `legal-site` 文件夹拖入上传区域。
3. 部署完成后使用 Netlify 提供的公开地址。
4. 也可以在 `Site configuration` 中绑定自定义域名。

## 填写到 Google Play Console

- **隐私权政策**：填写 `privacy-policy.html` 的最终公开 URL。
- **用户协议**：可以填写 `terms-of-service.html` 的公开 URL，放在商店详情、开发者网站或游戏官网中。
- **开发者联系邮箱**：确保与隐私政策和用户协议中提到的联系渠道一致。
- **数据安全表单**：根据实际接入的 SDK 和数据处理行为填写；不要只依据本页面文字，应以最终构建包内的 SDK 和数据流为准。

## 本地预览

直接双击 `index.html` 即可在浏览器中预览。若需要验证相对链接和移动端显示，可在本目录运行任意静态文件服务器，例如：

```powershell
python -m http.server 8080
```

然后访问 `http://localhost:8080/`。
