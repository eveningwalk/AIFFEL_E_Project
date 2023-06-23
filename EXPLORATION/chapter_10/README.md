- 코더 : 남희정
- 리뷰어 : 김경훈

----------------------------------------------

PRT(PeerReviewTemplate)

- [ ] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?

> * semantic segmentation mask의 오류를 보완할 수 있는 솔루션을 이유와 함께 제시하지 않았습니다.

- [X] 주석을 보고 작성자의 코드가 이해되었나요?
- [ ] 코드가 에러를 유발할 가능성이 있나요?
- [X] 코드 작성자가 코드를 제대로 이해하고 작성했나요? (직접 인터뷰해보기)
- [X] 코드가 간결한가요?

----------------------------------------------

참고 링크 및 코드 개선

* 크로마키 코드

``` python

def chroma_key_mode(_img_path, _S_Model, _LABEL_NAMES, _colormap, _object, _background_img):
    segvalues, output = model.segmentAsPascalvoc(_img_path)

    img_orig = cv2.imread(_img_path)
    img_orig_resize = cv2.resize(_background_img, (img_orig.shape[1], img_orig.shape[0]))
    
    index = _LABEL_NAMES.index(_object)
    seg_color = (_colormap[index][2], _colormap[index][1], _colormap[index][0])
    seg_map = np.all(output==seg_color, axis=-1) 
    
    img_mask = seg_map.astype(np.uint8) * 255
    img_mask_color = cv2.cvtColor(img_mask, cv2.COLOR_GRAY2BGR)
    img_bg_mask = cv2.bitwise_not(img_mask_color)
    
    return cv2.cvtColor(cv2.copyTo(img_orig_resize, img_bg_mask, img_orig), cv2.COLOR_BGR2RGB)
    
```
