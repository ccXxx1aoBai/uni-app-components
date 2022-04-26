* action-sheet 底部弹出框(列表)
* description 该组件一般用于餐饮酒店类用户地址选择
* address {Array} 地址列表数据
* mode {String} 有无圆角 默认md 可选 ios
* @updateLocation 用于修改父组件 地址信息（当选取位置完成后调用此方法）（传入数据 == 当前选取位置）
* <l-action-sheet ref="action" :address="address" mode="md" @updateLocation="updateLocation"></l-action-sheet>
* 通过$refs 调用show 和 hide 方法