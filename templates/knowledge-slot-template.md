```json
{
  "id": "slot-xxx",
  "title": "知识槽位标题",
  "question": "执行完成后需要回答的单一问题",
  "kind": "procedure",
  "targetNodeId": "node-id",
  "requiredEvidence": ["实际执行结果", "来源或文件路径", "适用边界"],
  "destinationHint": "inbox"
}
```

**使用说明：**

- `id`：唯一标识，格式 `slot-<主题>-<序号>`
- `title`：这个槽位要解决什么知识问题
- `question`：洞意阶段需要回答的具体问题
- `kind`：从以下选一个 — `principle` / `procedure` / `decision_rule` / `data_contract` / `verified_finding` / `risk_boundary` / `open_question`
- `targetNodeId`：可选，碎片挂载到哪个模块或评估对象
- `requiredEvidence`：洞意阶段必须收集哪些证据
- `destinationHint`：可选，建议碎片存到哪个分类（`inbox` / `tech-evaluation` / `architecture` 等）
- `status`：`candidate`（待验证）/ `verified`（有证据）/ `deprecated`（已过时）
- `confidence`：有证据 0.7-1.0，无证据 ≤ 0.6
