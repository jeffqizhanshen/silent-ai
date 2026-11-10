# 04 传感器候选与采购核查

核查日期：2026-11-10。厂家规格是特定条件的标称值；实验夹具、皮肤及多传感器条件尚未验证。库存/价格仅是检索页面快照，并非实时承诺，采购前重新核实中国配送、税费、库存、替代料和真实性；未下单。

| 候选 | 工作范围 / 速率 | 功耗与接口 | 用途和限制 |
|---|---|---|---|
| [ST VL53L1X](https://www.st.com/resource/en/datasheet/vl53l1x.pdf) | 确保最小 4 cm，最大 4 m（条件相关），最快 50 Hz；小于 4 cm 测量不准确 | 2.8 V、I²C；测距平均典型 16 mA，10 Hz/33 ms 平均功耗最大 20 mW；条件见表 15 | ToF 台架对照；脸部间距可能不满足；50 Hz 不保证所有模式、配置或多路并发 |
| [Vishay VCNL4040](https://www.vishay.com/en/product/84274/) | [产品系列资料](https://www.vishay.com/docs/49820/ms7493_proximitysensors_vcnl.pdf)列接近检测 0.2 m；并非毫米测距，近距离有效范围取决于表面/几何；[应用说明](https://www.vishay.com/docs/84307/designingvcnl4040.pdf)1T、1/40 示例约 4.85 ms/次 | I²C；100 mA 峰值 LED、1/40 示例 LED 平均 2.5 mA，不含整机；受设置影响 | 近距反射强度候选；漂移、饱和、肤色和环境光影响待测 |
| [Bosch BMI270](https://www.bosch-sensortec.com/media/boschsensortec/downloads/datasheets/bst-bmi270-ds000.pdf) | 加速度 0.78–1600 Hz、陀螺 25–6400 Hz ODR，实际有效频宽依配置 | I²C/SPI；典型 685 µA（全 ODR 无混叠条件） | 测镜架运动；不是直接测下颌位移；验证补偿净收益 |
| [Nordic nRF5340](https://www.nordicsemi.com/products/nrf5340) | MCU，采样率取决于外设、总线和固件，不适用测距 | BLE、I²C/SPI 等；[射频 TX](https://docs.nordicsemi.com/r/bundle/ps_nrf5340/page/chapters/current_consumption/doc/current_consumption.html) 0 dBm/1 Mbps 典型 4.1 mA（指定条件），非整机平均电流 | DK 作为候选采集平台；Zephyr、BLE 及吞吐待验证 |
| [MyoWare 2.0](https://www.sparkfun.com/myoware-2-0-muscle-sensor-wireless-kit.html) | 模拟 raw / rectified / envelope；频响和 ADC 采样须依最终电路核对，计划 raw 1 kHz 起测并验证抗混叠 | 模拟输出；传感器电流、频响和整系统功耗待核实实测 | sEMG 探索候选；电极位置、皮肤接触及人体安全先评审；并非医疗设备 |

AD8232 是 [ECG/生物电前端](https://www.analog.com/media/en/technical-documentation/data-sheets/ad8232.pdf)，典型 170 µA、模拟输出，**不是现成验证过的面部 sEMG 方案**；滤波、增益及采样必须重设计和验证，不推荐直接接人。

## 可采购性（仅查询快照）

| 物品 | 建议数量 | 查询情况 |
|---|---:|---|
| nRF5340 DK | 1 | [DigiKey 中国列表](https://www.digikey.cn/en/products/filter/evaluation-boards/rf-rfid-wireless-evaluation-boards/1165?s=N4Ig7CBcoIYE5QIwA5EGYA0IYBcmZAAcBLKAJgFYA2ABkQsSoF8mg)检索显示 256 件、¥404.82；库存变动、具体税费和结算待确认 |
| BMI270 转接板 SparkFun 22397 | 1–2 | [DigiKey 页面](https://www.digikey.cn/en/products/detail/sparkfun-electronics/22397/21703804)检索显示 838 件；价格与配送待确认 |
| VL53L1X 板 Adafruit 3967 | 1–2（对照，先核实几何） | [DigiKey 页面](https://www.digikey.cn/en/products/detail/adafruit-industries-llc/3967/17039169)检索显示 607 件、含税 ¥133.68/件；小于 4 cm 不准确 |
| VCNL4040 评估板 | 2–4 | 厂商提供 [样品/购买入口](https://www.vishay.com/en/product/84274/)；具体板型、库存、价格、配送尚未核实 |
| sEMG 无线套件、电极 | 按安全审查后决定 | [厂商页面](https://www.sparkfun.com/myoware-2-0-muscle-sensor-wireless-kit.html)有产品介绍；中国实际库存、价格和电极适配未核实 |
| 可调镜架/固定件、同步 LED、相机、供电测量仪 | 各 1 套 | 优先使用已有设备；供应商、精度、成本待核实 |

库存数来自搜索索引而非已完成购物车核验，可能滞后。需采购前复核；未核实的项目不得写成有货。
