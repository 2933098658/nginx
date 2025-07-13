以下是 NGINX 项目贡献指南的简体中文翻译：

------

# 贡献指南

以下是为 NGINX 项目贡献代码的一套指南。我们衷心感谢您考虑参与贡献！

## 目录

- [提出疑问](https://tencent.yuanbao/chat?from=launch&conversation=239ecb0d-2bcf-4b89-b75b-83068dd4b9c0&project_id=&project_name=#提出疑问)
- [报告缺陷](https://tencent.yuanbao/chat?from=launch&conversation=239ecb0d-2bcf-4b89-b75b-83068dd4b9c0&project_id=&project_name=#报告缺陷)
- [建议功能或改进](https://tencent.yuanbao/chat?from=launch&conversation=239ecb0d-2bcf-4b89-b75b-83068dd4b9c0&project_id=&project_name=#建议功能或改进)
- [发起讨论](https://tencent.yuanbao/chat?from=launch&conversation=239ecb0d-2bcf-4b89-b75b-83068dd4b9c0&project_id=&project_name=#发起讨论)
- [提交拉取请求](https://tencent.yuanbao/chat?from=launch&conversation=239ecb0d-2bcf-4b89-b75b-83068dd4b9c0&project_id=&project_name=#提交拉取请求)
- [问题生命周期](https://tencent.yuanbao/chat?from=launch&conversation=239ecb0d-2bcf-4b89-b75b-83068dd4b9c0&project_id=&project_name=#问题生命周期)

------

## 提出疑问

如需提问，请在 GitHub 上创建一个带有 `question` 标签的问题。

------

## 报告缺陷

如需报告缺陷，请使用预设的缺陷报告模板，在 GitHub 上创建一个带有 `bug` 标签的问题。报告前请确认该问题尚未被提交。

------

## 建议功能或改进

如需建议新功能或改进，请使用预设的功能请求模板，在 GitHub 上创建带有 `feature` 或 `enhancement` 标签的问题。请确保该建议尚未被提出。

------

## 发起讨论

若想与社区和维护者交流，我们鼓励您使用 [GitHub Discussions](https://github.com/nginx/nginx/discussions) 平台。

------

## 提交拉取请求

请按以下步骤贡献代码变更：

1. **Fork** NGINX 代码库
2. **创建新分支**
3. **在该分支上实现变更**
4. **完成测试后提交拉取请求 (PR)** 等待评审

编码问题请参考 [NGINX 开发指南](https://nginx.org/en/docs/dev/development_guide.html)

### 代码格式要求

1. **代码风格统一**
    变更需符合 [NGINX 代码风格规范](https://nginx.org/en/docs/dev/development_guide.html#code_style)。若无明确规定，请模仿现有代码风格。风格一致的变更更易被采纳。
2. **提交历史规范**
   - 保持分支提交历史**简洁清晰**
   - 本地执行变基操作（rebasing），将修改**按逻辑拆分成多个提交**
   - 提交信息格式：
     - 首行为**不超过67字符**的主题行
     - 空行后接详细描述（每行**不超过76字符**）
3. **提交主题前缀**
    对特定模块的修改需添加前缀，例如：
    `Upstream: 修复连接池泄漏`
    `QUIC: 新增超时控制`
    `Core: 优化内存分配`
    更多前缀请参考历史提交记录
4. **关联问题**
    在主题行引用相关 issue。如修复问题，请按 [GitHub 规范](https://docs.github.com/en/issues/tracking-your-work-with-issues/linking-a-pull-request-to-an-issue)标注 issue 编号

### 提交前须知

1. **平台兼容**
    变更需在 [所有支持平台](https://nginx.org/en/index.html#tested_os_and_platforms) 上正常运行

2. **说明变更必要性**
    清晰阐述修改原因，尽可能提供**使用场景示例**​

3. **测试验证**
    建议通过测试套件验证变更，防止功能退化。测试库克隆命令：

   ```
   git clone https://github.com/nginx/nginx-tests.git
   ```

4. **许可授权**
    提交即表示您授权项目在 [BSD-2-Clause 许可证](https://github.com/nginx/nginx/blob/master/LICENSE) 下使用该贡献

------

## 问题生命周期

为平衡 NGINX 工程团队工作与社区参与，问题处理流程如下：

1. **问题创建**
    社区成员新建 issue
2. **负责人分配**
    NGINX 工程团队指定负责人**全程跟进**​
3. **标签标注**
    负责人添加相应 [标签](https://github.com/nginx/nginx/issues/labels) 分类
4. **里程碑规划**
    负责人协同团队（产品与工程）确定所属里程碑，通常对应**产品版本发布计划**​

------

### 术语对照表

| 英文术语        | 中文译法     |
| --------------- | ------------ |
| Pull Request    | 拉取请求     |
| Rebasing        | 变基         |
| Commit history  | 提交历史     |
| Subject line    | 主题行       |
| Issue lifecycle | 问题生命周期 |
| Milestone       | 里程碑       |
| Regression      | 功能退化     |
| Upstream        | 上游模块     |
| Test suite      | 测试套件     |

此翻译严格遵循技术文档的准确性要求，同时优化了长句结构（如拆分被动语态为主动表述），保留原链接确保可操作性，并采用符合中文技术文档习惯的表述方式（如“拉取请求”、“变基”等通用译法）。关键流程条目使用数字编号增强可执行性。