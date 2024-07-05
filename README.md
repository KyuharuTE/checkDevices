## checkDevices
这是一个监测安卓设备的 Py 脚本，您可以直接在您的 Py 项目上调用它

## 必备文件
- src 中的所有文件
- checkDevices.py 脚本

## 编写环境
- Windows 11
- VsCode
- Python 3.12

## 如何使用
```python
from checkDevices import checkDevices

# 本函数包括三个参数:
# - mode(检测的模式(Str): device, fastboot, recovery 等；可选；若选择则只返回符合模式的设备或设备数量)
# - maxDevices(最大设备数量(int): 大于 0 的整数；若有此参数则会先检测设备总数量，若超过设置数量则返回 -2)
# - needList(是否返回列表(bool): True/False；若选择 True 则返回设备列表，反之返回设备数量)
devices = checkDevices("device", 1, False)
# 若总连接设备数量等于 1 时，且设备在开机状态下返回 1

devices = checkDevices("device", 1, True)
# 若总连接设备数量等于 1 时，且设备在开机状态下返回一个包含多个 Device 对象的列表
devices[0].name # 获取第一个设备的序列号
devices[1].status # 获取第二个设备的状态
```

## 返回详解
- -1：无设备连接（任何模式都没）
- -2：设备数量超出指定范围
- 0：有连接设备，但处于指定模式下的设备为 0
- 大于等于 1 的整数：处于指定模式下的设备数量
- 含 Device 对象的列表：设备列表
