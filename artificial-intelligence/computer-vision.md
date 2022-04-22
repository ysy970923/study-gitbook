---
cover: >-
  https://images.unsplash.com/photo-1552664730-d307ca884978?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=2970&q=80
coverY: 0
---

# Computer Vision

### Various Convolution methods ([referred to](https://eehoeskrap.tistory.com/431))

#### Seperable Convolution

* breaks 1 kernel into 2 kernels (ex. 3\_3 -> 3\_1, 1\*3)

#### Depthwise Convolution

* 1 filter per 1 channel
* same as Grouped Convolution with n\_input\_channel groups

#### Depthwise Separable Convolution

* Depthwise Convolution + additional size 1 convolution
