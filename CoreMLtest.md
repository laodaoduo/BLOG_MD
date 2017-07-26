---
title: CoreMLtest
date: 2017-07-26 16:53:25
tags: Swift
---
iOS 11 机器学习练习

<!--more-->

##  iOS 11 机器学习练习
<!---->
<!---->
### 图片数据
``` oc
let imageData = pickImageView.image?.cgImage

```
### 用到的模型
``` oc
let model = try! VNCoreMLModel(for: Resnet50().model)

```
### 配置请求
``` oc
let hander = VNImageRequestHandler(cgImage: imageData!)
let request = VNCoreMLRequest(model: model, completionHandler: myResultsMethod)
```

### 执行请求
```
try! hander.perform([request])
```
### 请求的方法 用于model的输入输出
``` javascript
func myResultsMethod(request: VNRequest, error: Error?) {
guard let results = request.results as? [VNClassificationObservation]
else { fatalError("huh") }
lable.text = results[0].identifier
for classification in results {
print("=====++===" + classification.identifier + "----++----" )
}

}
```


```podfile

platform :ios, "8.0"
inhibit_all_warnings!

use_frameworks!
target 'RAC_ObjcTest' do

pod 'ReactiveObjC'
pod 'XRCarouselView'

end

```
