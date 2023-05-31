## **Code Peer Review Templete**
------------------
- 코더 : 남희정
- 리뷰어 : Donggyu Kim

## **PRT(PeerReviewTemplate)**
------------------  
- [O] **1. 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?**

Everything was **DONE**. 
1. The dataset necessary for learning the pix2pix model was properly constructed. (Done)
2. The pix2pix model was implemented and the learning process was successfully carried out. (Done)
3. Visualization results for the learning process and testing were submitted. (Done)

- [O] **2. 주석을 보고 작성자의 코드가 이해되었나요?**

Thanks to the comments like below, I can understand what she want to do.
```python
# For문을 활용해서 DiscBlock을 쌓아주세요.
# 조건 1 : 3번째까지 stride는 2로 주되 이후에는 1로 주세요
# 조건 2 : 3번째까지 custom padding을 주지 않아도 되는데 이후에는 주세요.
# 조건 3: 1번째와 5번째에서는 Batch Normalization을 사용하지 마세요.
# 조건 4 : 1번째부터 4번째까지 LeakyReLU를 적용하고 마지막에는 sigmoid를 적용하세요. (sigmoid의 경우 따로 정의해야 합니다)
```

And she used markdown cell to explain the code.
```markdown
1. 두이미지를 concatenate하고, padding후, crop
2. 좌우 반전
3. 위아래 반전
4. 회전
```
I think that it is one of good way because it is a Jupyter Notebook, not a code.

- [x] **3. 코드가 에러를 유발할 가능성이 있나요?**

Every code, every class were clean, simple, understadable, and acceptable.
```python
class DiscBlock(layers.Layer):
    def __init__(self, n_filters, stride=2, custom_pad=False, use_bn=True, act=True):
        super(DiscBlock, self).__init__()
        self.custom_pad = custom_pad
        self.use_bn = use_bn
        self.act = act
        
        if custom_pad:
            self.padding = layers.ZeroPadding2D()
            self.conv = layers.Conv2D(n_filters, 4, stride, "valid", use_bias=False)
        else:
            self.conv = layers.Conv2D(n_filters, 4, stride, "same", use_bias=False)
        
        self.batchnorm = layers.BatchNormalization() if use_bn else None
        self.lrelu = layers.LeakyReLU(0.2) if act else None
        
    def call(self, x):
        if self.custom_pad:
            x = self.padding(x)
            x = self.conv(x)
        else:
            x = self.conv(x)
                
        if self.use_bn:
            x = self.batchnorm(x)
            
        if self.act:
            x = self.lrelu(x)
        return x 
```
For example, the class is a Discriminator's layer.
Because she tried to consider **READABILITY**, there are some new-line and snake-case for some attributes names.
In addition, It was well-organized structurally, so my eyes was comfortable, and my brain too.

- [O] **4. 코드 작성자가 코드를 제대로 이해하고 작성했나요?**

Q: Unlike the official example in the TF, in your code, you seem to use Subclassing api. So, what is best pros for you.

A: It would be nice to be able to use object orientation.

Q: In the denormalize function, you used uint8 for return array's type. Why you use it.

A: Color values range from 0 to 255, and all normalized values are based on color values, so I used them to optimize memory capacity.

- [O] **5. 코드가 간결한가요?**

By using if-else expression in the for-loop statements to create a various of Blocks for the Discriminator, she maximized the simplity of her code. 
It was an "amazing" idea, I believe.
```python
for i, fts in enumerate(filters):   #hjnam
    self.blocks.append(DiscBlock(
        n_filters = fts,
        stride = 1 if i > 2 else 1,
        custom_pad = False if i > 3 else True,
        use_bn = False if i == 1 or i == 5 else True,
        act = True if i >= 4 else False
        ))
```

## **참고링크 및 코드 개선 여부**
What is the difference between Layer and Model
- https://stackoverflow.com/questions/55109696/tensorflow-difference-between-tf-keras-layers-layer-vs-tf-keras-model
- https://stackoverflow.com/questions/56963060/keras-what-is-the-difference-between-model-and-layers

(Maybe you can find better refers:) )

    
