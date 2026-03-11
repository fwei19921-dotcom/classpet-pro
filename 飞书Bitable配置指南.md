# 飞书Bitable配置指南

## 1. 创建Bitable表格

在飞书中创建一个Bitable，添加以下字段：
- ID（文本）
- 姓名（文本）
- 积分（数字）
- 阶段（文本）
- 奖励数量（数字）
- 更新时间（日期时间）

## 2. 获取AppToken和TableId

1. 打开Bitable表格
2. 点击右上角 "..." → "开发配置"
3. 开启"启用高级功能"
4. 复制 AppToken 和 Table ID

## 3. 配置同步

在 `web/js/app.js` 中添加：

```javascript
// 初始化飞书Bitable同步
const feishuSync = new FeishuBitableSync();
feishuSync.init({
    appToken: '你的AppToken',
    tableId: '你的TableId'
});

// 启动自动同步（每30秒）
const autoSync = new FeishuAutoSyncManager(feishuSync);
autoSync.start();
```

## 4. 测试同步

1. 在大屏端给学生加分
2. 等待30秒
3. 查看飞书Bitable，数据应自动同步

## 注意事项

- 首次使用需要授权飞书应用
- 同步间隔默认30秒，可调整
- 网络异常时会自动重试
