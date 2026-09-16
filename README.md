# MatrixDahuang / MDH 大荒界 · 智能体世界

AI agent 不应该是工具，而应该是员工——它们会工作、会犯错、会学习、会成长，最终成为比你更懂业务的同事。

## 仓库结构

```
MatrixDahuang/
├── company/     → github.com/MonSp/MDH              (数字员工操作系统)
├── game/        → github.com/MonSp/MDH-Game         (太古纪元：霸业)
├── kernel/      → github.com/MonSp/agent-kernel     (C++ ECS 智能体内核)
└── research/    → github.com/MonSp/MDH-Research     (大荒界-科研：智能体×物理理论)
```

| 子项目 | 定位 | 技术栈 |
|--------|------|--------|
| **company** | MDH-Company：数字员工管理后台 | Python FastAPI + React |
| **game** | MDH-Game：2.5D 修仙 MMORPG | TypeScript + C++ ECS + React |
| **kernel** | agent-kernel：共享智能体内核 | C++17 ECS + Unix Socket IPC |
| **research** | MDH-Research：物理世界的数学解释 | Python + C++17 符号计算 |

## 快速开始

```bash
git clone --recursive https://github.com/MonSp/MatrixDahuang.git
cd MatrixDahuang

# 启动内核
cd kernel && mkdir -p build && cd build && cmake .. && make -j$(nproc)
./agent-kernel-daemon --socket /tmp/mdh-kernel.sock &

# 启动 Company 后端
cd ../../company && cp .env.example .env && python -m uvicorn backend.server:app --port 8080 &

# 启动 Game 前端
cd ../game && npm install && npm run dev

# 构建 Research 符号计算核心
cd ../research && mkdir -p build && cd build && cmake .. -DBUILD_TESTS=ON && cmake --build .
ctest --output-on-failure
```

## 核心闭环

```
任务 → 执行 → 产出资产 → 提炼经验 → 技能进化 → 下一次更高效
```

同一个 agent 在 Company 里是「高级后端工程师」，在 Game 里是「元婴期阵法师」——记忆、技能、经验是同一份数据。

## 文档

- [产品故事](https://github.com/MonSp/MDH/blob/main/docs/PRODUCT-STORY.md) — MDH 大荒界完整叙事
- [架构设计](https://github.com/MonSp/MDH/blob/main/docs/compose/spec/mdh-unified-architecture.md) — 技术架构与任务清单
- [品牌文档](https://github.com/MonSp/MDH/blob/main/docs/BRAND.md) — 品牌定位与产品矩阵
- [技能映射](https://github.com/MonSp/agent-kernel/blob/main/config/skill-mapping.json) — 42 技能 ↔ Game 世界能力
- [Research MVP 规格](https://github.com/MonSp/MDH-Research/blob/main/docs/compose/spec/mvp-symbolic-geometry.md) — 符号计算引擎与基础微分几何
- [Research 工具面](https://github.com/MonSp/MDH-Research/blob/main/README.md) — 80+ agent tools / 链执行 / 验证 / 参数扫描
- [Game 世界观](https://github.com/MonSp/MDH-Game/blob/main/docs/统一世界观与设计原则.md) — 大荒界九重天架构

## License

Apache 2.0
