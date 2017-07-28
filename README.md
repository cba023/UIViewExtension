# UIViewExtension

## Swift开发中快速实现视图坐标调整的UIView扩展方法（Swift developing rapidly for view coordinates adjustment UIView extension methods）

直接通过赋值实现视图的布局转换。Now you directly through the assignment to achieve the layout of the view transformation.



### size

```
/// 尺寸
var size: CGSize {
get {
return self.frame.size
}
set(newValue) {
self.frame.size = CGSize(width: newValue.width, height: newValue.height)
}
}
```

### width

```
/// 宽度
var width: CGFloat {
get {
return self.frame.size.width
}
set(newValue) {
self.frame.size.width = newValue
}
}
```

### height

```
/// 高度
var height: CGFloat {
get {
return self.frame.size.height
}
set(newValue) {
self.frame.size.height = newValue
}
}
```

### x

```
/// 横坐标
var x: CGFloat {
get {
return self.frame.minX
}
set(newValue) {
self.frame = CGRect(x: newValue, y: y, width: width, height: height)
}
}
```

### y

```
/// 纵坐标
var y: CGFloat {
get {
return self.frame.minY
}
set(newValue) {
self.frame = CGRect(x: x, y: newValue, width: width, height: height)
}
}

```

### right

```
/// 纵坐标
var y: CGFloat {
get {
return self.frame.minY
}
set(newValue) {
self.frame = CGRect(x: x, y: newValue, width: width, height: height)
}
}
```


### bottom

```
/// 底端纵坐标
var bottom: CGFloat {
get {
return frame.origin.y + frame.size.height
}
set(newValue) {
frame.origin.y = newValue - frame.size.height
}
}
```

### centerX

```
/// 中心横坐标
var centerX: CGFloat {
get {
return self.center.x
}
set(newValue) {
center.x = newValue
}
}
```

### centerY
```
/// 中心纵坐标
var centerY: CGFloat {
get {
return center.y
}
set(newValue) {
center.y = newValue
}
}
```

### origin

```
/// 原点
var origin: CGPoint {
get {
return self.origin
}
set(newValue) {
frame.origin = newValue
}
}
```

### topRight

```
/// 右上角坐标
var topRight: CGPoint {
get {
return CGPoint(x: frame.origin.x + frame.size.width, y: frame.origin.y)
}
set(newValue) {
frame.origin = CGPoint(x: newValue.x - width, y: newValue.y)
}
}

```

### bottomRight

```
/// 右下角坐标
var bottomRight: CGPoint {
get {
return CGPoint(x: frame.origin.x + frame.size.width, y: frame.origin.y + frame.size.height)
}
set(newValue) {
frame.origin = CGPoint(x: newValue.x - width, y: newValue.y - height)
}
}

```

### bottomLeft 

```
/// 左下角坐标
var bottomLeft: CGPoint {
get {
return CGPoint(x: frame.origin.x, y: frame.origin.y + frame.size.height)
}
set(newValue) {
frame.origin = CGPoint(x: newValue.x, y: newValue.y - height)
}
}
```

###  剪掉一个方向的部分距离。To cut off in one direction some distance

```
/// 获取UIView对象某个方向缩进指定距离后的方形区域
///
/// - Parameters:
///   - direction: 要缩进的方向
///   - distance: 缩进的距离
/// - Returns: 得到的区域
func cutRect(direction: Direction, distance: CGFloat) ->  CGRect {
switch direction {
case .top:
return CGRect(x: 0, y: distance, width: self.width, height: self.height - distance)
case .left:
return CGRect(x: distance, y: 0, width: self.width - distance, height: self.height)
case .right:
return CGRect(x: 0, y: 0, width: self.width - distance, height: self.height)
case .bottom:
return CGRect(x: 0, y: 0, width: self.width, height: self.height - distance)
}
}
```
