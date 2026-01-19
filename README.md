# EdgePress 静态站点部署仓库

**本项目参加阿里云天池 ESA Pages 边缘开发大赛**

**本项目由阿里云ESA提供加速、计算和保护**

![阿里云ESA](https://img.alicdn.com/imgextra/i3/O1CN01H1UU3i1Cti9lYtFrs_!!6000000000139-2-tps-7534-844.png)

这是 [EdgePress WordPress 主题](https://github.com/nike022/EdgePress) 的静态站点部署仓库，展示了如何将 WordPress 站点完全静态化并部署到阿里云 ESA Pages 边缘平台。

## 在线演示

- **在线访问**: https://wp-blog.e4dd06ac.er.aliyun-esa.net
- **主题源码**: https://github.com/nike022/EdgePress
- **本仓库地址**: https://github.com/nike022/wp-blog

## 项目简介

EdgePress 是一个专为静态站点生成优化的 WordPress 主题，突破了传统 WordPress 必须依赖服务器的限制。用户可以在本地使用 WordPress 的所有功能，通过免费的 Simply Static 插件生成静态文件，推送到 GitHub 后由 ESA Pages 自动部署，实现零服务器成本的全球边缘加速访问。

## 双仓库结构说明

本项目采用双仓库结构，既展示了开发过程，又提供了可部署的最终产物：

### 1. WordPress 主题源码仓库
- **地址**: https://github.com/nike022/EdgePress
- **内容**: 完整的 WordPress 主题源代码
- **作用**: 展示针对静态化的优化工作、自定义功能和小工具

### 2. 静态站点仓库（本仓库）
- **地址**: https://github.com/nike022/wp-blog
- **内容**: Simply Static 生成的静态 HTML 文件 + Pagefind 搜索索引
- **作用**: 实际部署到 ESA Pages 的内容，展示最终产物

## 核心创新

### 🎯 突破 Simply Static 免费版限制

Simply Static 付费版才有的功能，我们已经免费实现：

**1. 静态搜索功能** ✅
- 付费版功能：需要升级才能使用搜索
- EdgePress 方案：集成 Pagefind 静态搜索，完全免费
- 优势：支持中文全文搜索、即时响应、深色模式

**2. 评论系统** ✅
- 付费版功能：需要升级才能集成第三方评论
- EdgePress 方案：集成 Waline 边缘评论系统，完全免费
- 优势：实时评论、浏览量统计、表情支持

**3. 内容加密** ✅
- EdgePress 独有：AES-256-CBC 加密，支持公众号引流和付费内容
- 优势：静态 HTML 中实现内容保护，支持多种变现方式

### 💡 完整的 WordPress 体验 + 零服务器成本

**无需放弃 WordPress 的任何功能**：
- ✅ 在本地安装 WordPress，使用熟悉的后台管理界面
- ✅ 使用可视化编辑器发布和管理文章
- ✅ 使用插件、主题、小工具等所有 WordPress 功能
- ✅ 完整的分类、标签、菜单管理

**无需服务器和数据库**：
- ✅ 本地运行 WordPress（XAMPP/MAMP/LocalWP）
- ✅ 使用免费的 Simply Static 插件生成静态文件
- ✅ 推送到 GitHub，ESA Pages 自动部署
- ✅ 零服务器成本，无需维护 PHP 和 MySQL

## 工作流程

```
本地 WordPress 编辑文章
    ↓
Simply Static 生成静态文件（免费版）
    ↓
推送到 GitHub（包含 esa.jsonc）
    ↓
ESA Pages 自动部署（自动执行 pagefind 构建）
    ↓
全球边缘加速访问
```

**整个流程完全免费，无需任何付费插件或服务器！**

## 本仓库内容

- **静态 HTML 文件**: 由 Simply Static 从 WordPress 生成
- **Pagefind 搜索索引**: 由 ESA Pages 在部署时自动构建
- **esa.jsonc 配置文件**: ESA Pages 构建配置

### esa.jsonc 配置

```json
{
  "buildCommand": "npx pagefind --site .",
  "assets": {
    "directory": "."
  }
}
```

这个配置告诉 ESA Pages：
- 在部署时自动执行 `npx pagefind --site .` 生成搜索索引
- 将根目录作为静态资源目录进行托管

## 技术特点

### 1. 静态化优化
- **完美的路径兼容**: 自动处理 `.html` 后缀，确保静态站点链接正确
- **分页链接适配**: 分页链接自动适配静态路径
- **JavaScript 模块化**: 避免 Simply Static 转义问题

### 2. 边缘功能集成
- **Waline 评论系统**: 集成边缘评论服务，静态站点也能实时互动
- **浏览量统计**: 基于 Waline API 的边缘统计，无需后端数据库
  - 静态 HTML 中嵌入 `<span class="waline-pageview-count">` 元素
  - 通过 JavaScript 调用 Waline API 实时获取和更新浏览量
  - 文章详情页自动增加浏览量，列表页仅显示浏览量
  - 完全基于边缘计算，无需 WordPress 数据库支持
- **内容加密**: AES-256-CBC 加密，静态 HTML 中实现付费内容保护

### 3. Pagefind 静态搜索
- **零后端依赖**: 搜索索引在构建时生成，无需服务器支持
- **中文优化**: 完整的中文分词和搜索支持
- **即时搜索**: 输入即搜索，无需等待
- **深色模式适配**: 搜索界面自动适配深色模式
- **ESA Pages 自动构建**: 通过 esa.jsonc 配置，部署时自动生成搜索索引

### 4. 性能优势
- **零服务器成本**: 纯静态 HTML，无需 PHP 和 MySQL
- **全球边缘加速**: 部署在阿里云 ESA Pages，访问速度极快
- **首屏加载时间**: < 1s（ESA Pages 边缘加速）
- **Lighthouse 评分**: 95+ (Performance)

## 技术栈

- **前端框架**: Tailwind CSS 3.4
- **JavaScript**: 原生 ES6+
- **评论系统**: Waline（边缘评论服务）
- **静态搜索**: Pagefind
- **加密算法**: CryptoJS (AES-256-CBC)
- **静态化工具**: Simply Static（免费版）
- **部署平台**: 阿里云 ESA Pages

## 部署说明

本仓库通过 GitHub 与 ESA Pages 关联，实现自动部署：

1. 推送代码到本仓库
2. ESA Pages 自动检测 `esa.jsonc` 配置
3. 执行 `npx pagefind --site .` 生成搜索索引
4. 部署静态文件到全球边缘节点
5. 通过 `*.er.aliyun-esa.net` 域名访问

## 项目亮点

### 创意卓越 🎨
- 突破 Simply Static 免费版限制，免费实现搜索和评论功能
- 完整的 WordPress 体验 + 零服务器成本
- 极简工作流程，完全免费

### 应用价值 💡
- 零服务器成本，适合个人博客、企业官网、文档站点
- 极致性能，全球访问速度提升 10 倍以上
- 开箱即用，提供完整的小工具系统

### 技术探索 🚀
- 静态化优化技术（Tailwind JIT、路径兼容、JavaScript 模块化）
- 边缘功能集成（Waline 评论、浏览量统计、内容加密）
- Pagefind 静态搜索（零后端依赖、中文优化、ESA Pages 自动构建）
- 完美的静态化支持（分页链接、评论系统、JavaScript 代码）

## 相关链接

- [EdgePress 主题源码](https://github.com/nike022/EdgePress)
- [阿里云 ESA Pages](https://www.aliyun.com/product/esa)
- [Simply Static 插件](https://wordpress.org/plugins/simply-static/)
- [Pagefind 搜索引擎](https://pagefind.app/)
- [Waline 评论系统](https://waline.js.org/)

## 许可证

GPL-2.0 License

本项目基于 [Less Theme](https://github.com/xzmhxdxh/Less) 进行二次开发和优化。

---

**感谢阿里云 ESA 提供的边缘计算平台支持！**
