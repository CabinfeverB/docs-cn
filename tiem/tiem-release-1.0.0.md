---
title: TiDB Enterprise Manager v1.0.0 Release Notes
summary: 了解 TiEM v1.0.0 版本的发版说明。
---

# TiDB Enterprise Manager v1.0.0 Release Notes

发布日期：2022 年 4 月 7 日

TiEM 版本：1.0.0

> **注意：**
>
> TiEM v1.0.0 未开源。若要获取 v1.0.0 的安装包或相关支持，请联系 TiEM 团队。

TiDB Enterprise Manager (TiEM) 是一款以 TiDB 数据库为核心的数据库管理平台，帮助用户在私有部署 (on-premises) 或公有云环境中管理 TiDB 集群。

TiDB Enterprise Manager 不仅提供对 TiDB 集群的全生命周期的可视化管理，也同时一站式提供 TiDB 数据库参数管理、数据库版本升级、克隆集群、主备集群切换、数据导入导出、数据同步、数据备份恢复服务，能有效提高 TiDB 集群运维效率，降低企业运维成本。

## 用户价值

分布式数据库管理面临集群规模化、管理场景多元化挑战，传统的命令行管理方式面临部署成本高、技术门槛高、维护成本高等诸多挑战，TiEM 能有效解决以下场景中的分布式数据库管理难题：

- 主机资源管理
- 部署集群
- 统一入口管理多套集群
- 升级集群
- 参数管理
- 备份恢复
- 数据导入导出
- 安全与合规
- 自动化与第三方集成
- 管理任务历史记录可查可追溯

## 主要功能

### 集群主机资源管理

- 统一构建 TiDB 集群 IT 基础设施资源池，主机资源（vCPU、内存、磁盘）总量与分配用量一目了然。
- 支持按集群类型、组件类型对主机资源分类，让最合适的主机资源匹配不同 TiDB 组件，提升主机资源利用率。
- 支持按集群独立部署与混合部署对资源进行分类，支持在不同主机资源上灵活快速部署多套 TiDB 集群。
- 支持主机位置信息，区域（Region) - 可用区 （Available Zone) - 机架 （Rack）三层结构清楚定义主机位置。

### 集群全生命周期管理

- 支持一站式管理多套 TiDB 集群。

    一个 Web 入口统一管理多套 TiDB 集群，同时查看多套集群日志、监控和告警。

- 支持快速灵活部署 OLTP 集群和 HTAP 集群：

    - 一页配置集群，避免直接修改拓扑和配置文件，有效降低集群配置错误
    - 一键创建集群，缩短 88% 集群创建时间
    - 规范创建流程，降低技术门槛，自动检查创建流程每一步结果，确保数据库集群健康上线，及时响应业务需求

- 支持扩容、缩容 TiDB 集群：

    - 支持用户根据业务需要灵活调整 TiDB 集群规模，让数据库服务能力与业务规模保持动态适配
    - 集群扩缩容过程中，确保 TiDB 组件实例数量符合最佳实践
    - 支持异步完成 TiDB 集群缩容，确保 Region 数据迁移与集群缩容有序完成

- 支持一键重启、停止、删除 TiDB 集群：

    - 支持一键完成 TiDB 集群日常操作
    - 删除集群前，提醒用户进行最终备份，确保数据安全
    - 优化删除集群操作的用户交互，防呆设计有效避免集群误删除

- 统一集成数据库监控告警和 TiDB Dashboard。

    统一 Web 入口实时监控多套 TiDB 数据库性能，及时发现热点和 SQL 慢查询，帮助数据库管理员跟踪数据库核心指标，提前发现数据库潜在风险。

- 支持统一查看 TiDB 集群日志。

    统一查看多套 TiDB 集群日志，支持按组件、日志级别、时间范围、日志内容、IP 地址过滤日志，帮助数据库管理员快速完成根因定位。

- 支持接管由 TiUP 安装的 TiDB 集群。一键接管存量 TiDB 集群，统一入口管理新老集群，提高集群管理效率。

### 克隆集群与一键主备切换

- 支持一键克隆 TiDB 集群，快速构建主备集群

    支持一键克隆 TiDB 集群，快速构建主备集群，自动构建数据同步任务，确保主备集群间数据保持同步，有效缩短 90% 主备集群创建时间。

- 支持一键切换主备集群：

    - 帮助管理员快速完成主备集群切换，自动实现数据同步任务切换，提高数据库容灾能力及业务连续性
    - 主备切换过程中确保至少有一个集群始终可读，确保数据库服务不中断
    - 主备切换过程中确保数据不丢失

### TiDB 集群升级

- 支持 TiDB 集群可视化原地升级

    - 支持全流程可视化集群原地升级，简化数据库管理员的业务操作流程，提高集群升级成功率；
    - 提供集群升级前后参数对比，允许数据库管理员核查、选择参数，避免升级前后参数变化对集群性能的影响。

### 参数管理

- 提供 TiDB 版本对应参数组模板：

    - 根据 TiDB 最佳实践经验，内置 TiDB 版本对应的参数组模板，帮助数据库管理员快速完成集群参数优化
    - 支持用户可自定义参数组，沉淀积累运营中的最佳参数组合
    - 支持用户快速应用参数组至不同集群

- 提供统一界面查看、修改 TiDB 集群参数：

    - 统一管理不同接口的参数（SQL、TiUP、 各组件 API），屏蔽参数管理接口细节
    - 帮助数据库管理员随时查看、调整 TiDB 集群运行参数，降低参数管理维护难度
    - 通过参数值有效校验和定期巡检，减少参数错误对集群性能带来的负面影响

### 数据备份与恢复

- 支持手动备份 TiDB 集群，帮助数据库管理员随时触发备份请求，支持查看备份进度。
- 支持设置 TiDB 集群的自动备份策略，帮助数据库管理员设置周期性、自动化的备份策略，满足数据安全、审计的合规要求。
- 支持从备份数据恢复创建新 TiDB 集群，备份数据与创建集群与无缝对接，快速恢复集群与数据。
- 支持备份历史记录，方便数据库管理员查看历史备份记录，检查备份任务状态。

### 数据导入与导出

- 支持数据导入 TiDB 集群，从不同存储（S3 兼容存储、NFS存储、本地存储）快速导入全量数据到 TiDB 集群。

- 支持从 TiDB 集群导出数据：

    - 从 TiDB 集群导出 SQL 或 CSV 格式的数据，可存储与 S3 兼容的存储或 NFS 存储
    - 支持按库、表过滤导出数据
    - 支持按 SQL 语句过滤导出数据

- 支持跨 TiDB 集群导入和导出数据。

    不同 TiDB 集群之间，通过 TiEM 共享存储实现跨集群的数据全量导入与导出，完成数据流动与融合，打破数据孤岛，实现数据价值挖掘。

- 支持导入导出历史记录，方便数据库管理员查看数据导入导出历史记录，检查任务状态。

### 数据同步

支持 TiCDC 数据同步：

- 快速构建从 TiDB 集群到下游系统  (TiDB、MySQL、Kafka） 的数据同步任务
- 支持数据同步任务按库、表过滤
- 支持数据同步任务管理：创建、暂停、恢复、删除

### 工作流任务管理

- 自动记录管理员操作，历史任务事后可追查、可回溯，帮助数据库管理员查看集群历史任务记录，检查工作流执行进度与结果，快速分析操作失败原因。
- 规范不同场景下数据库管理员操作流程。规范数据库管理员在各场景下的操作流程，避免人工操作错误与遗漏。
- 支持异步工作流任务。管理员任务工作量支持异步，确保用户操作体验。

### OpenAPI（实验特性）

提供集群全生命周期 OpenAPI：

- 帮助管理员完成数据库管理自动化
- 实现 TiDB 管理信息与第三方平台集成