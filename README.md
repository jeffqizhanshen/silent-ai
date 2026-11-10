# Silent AI

Silent AI 是处于探索阶段的智能眼镜式无声中文交互研发项目。目标是在开放办公环境中，通过自然的无声发音动作生成中文文本，交由手机或 PC 上的大模型处理，并通过独立蓝牙耳机私密播放回答。**连续中文识别目前只是目标，不是已证明的能力。**

## 当前状态

- 当前里程碑：E01 传感器可行性设计；尚无采集数据、实验结果、固件、模型或产品性能指标。
- 产品约束：眼镜形态、无声输入、中文连续语言目标、手机/PC 计算、独立耳机输出。RGB 视频仅用于授权的实验室参考。
- 当前只初始化文档及实验方案；未采购、未开展人体采集，候选器件与架构均待验证。重大技术决策应解释证据并等待项目负责人确认。
- 数据默认本地存储；未经参与者及项目授权，不上传原始视频或生物信号。发送识别文本至外部 LLM 也须用户明确同意。

## 系统概览

```text
面部运动 → 眼镜候选传感器(IR/ToF、IMU、可选 sEMG)
 → 时间戳采集/传输 → 手机或 PC：同步、识别、置信度和确认
 → 用户授权的 LLM → 文本/语音合成 → 系统蓝牙耳机
实验室：独立参考视频及同步标记 → 本地数据集与离线评估
```

## 文档导航

1. [产品需求](docs/01-PRD.md) · [系统架构](docs/02-system-architecture.md)
2. [硬件架构](docs/03-hardware-design.md) · [器件与采购核查](docs/04-sensor-selection.md)
3. [算法](docs/05-algorithm-design.md) · [数据规范](docs/06-dataset-specification.md)
4. [研发计划](docs/07-development-roadmap.md) · [风险与验证](docs/08-risk-and-validation.md) · [决策日志](docs/09-decision-log.md)
5. [E01 实验方案](experiments/E01-sensor-validation/README.md) · [首批任务](docs/10-initial-tasks.md)

## 目录与使用

`hardware/` 放固件、原理图、PCB 与机械设计；`algorithm/` 放采集、预处理、模型、训练、评估；`application/` 放桌面与移动应用；`experiments/` 放预注册方案和结果。空目录的 `.gitkeep` 仅保留结构，不代表已有实现。当前无需安装依赖或运行命令；后续每个可运行模块须自行提供环境、版本、执行和验证说明。

从 [E01](experiments/E01-sensor-validation/README.md) 开始：先做无人体的台架测量和连接安全审查，再在取得同意后采集小规模试点；按预先冻结的拆分和门槛比较模态，汇报证据后由负责人决定是否进入下一里程碑。时间计划是可调整假设，不是交付承诺。
