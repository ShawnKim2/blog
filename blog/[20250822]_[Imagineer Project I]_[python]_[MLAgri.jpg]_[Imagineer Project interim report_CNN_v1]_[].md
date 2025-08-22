---

# 1. 프로젝트: CNN 기반 토마토 이미지 분류 모델

## 프로젝트 정보

* **주제:** 스마트팜 토마토 이미지 데이터를 활용한 CNN 기반 성숙도 분류 모델
* **사용 프레임워크:** TensorFlow / Keras
* **데이터 출처:** Google Drive에 저장된 `tomato_3000_v2` 데이터셋

<br/><br/><br/>

# 연구 개요

본 프로젝트는 **스마트팜에서 수집된 토마토 이미지를 CNN 모델로 학습하여, 토마토의 성숙 단계를 분류**하는 것을 목표로 한다.
데이터는 학습(Train), 검증(Validation), 테스트(Test) 세 가지로 분할하고, 이미지 증강 기법을 활용하여 모델의 일반화 성능을 높였다.

---

##소스코드

<p>
  <iframe
    src="https://nbviewer.org/gist/ShawnKim2/f44150d264401fa703a32963c717a0c2"
    width= "800px"
    height= "1000"
    frameborder="0"
    scrolling="yes">
  </iframe>
</p>


<br/><br/>

## 데이터 준비 단계

### Google Drive 연동

```python
from google.colab import drive
drive.mount('/content/drive')
```

Colab 환경에서 Google Drive를 마운트하여 데이터셋(`tomato_3000_v2`)을 불러온다.

### 경로 설정 및 클래스 확인

```python
data_dir = '/content/drive/MyDrive/smart_agriculture/tomato_3000_v2/train'
class_names = os.listdir(data_dir)
class_names = [cls for cls in class_names if not cls.startswith('.')]
class_names.sort()
print("클래스 목록:", class_names)
```

* 데이터셋 폴더 내부의 클래스명을 읽어옴
* 숨김파일(`.`)은 제외
* 항상 동일한 순서를 유지하기 위해 정렬 수행

---

## 데이터셋 분할

```python
trainval_paths, test_paths, trainval_labels, test_labels = train_test_split(
    image_paths, labels, test_size=0.1, stratify=labels, random_state=42
)
train_paths, val_paths, train_labels, val_labels = train_test_split(
    trainval_paths, trainval_labels, test_size=0.2, stratify=trainval_labels, random_state=42
)
```

* **Train+Val : Test = 90 : 10**
* **Train : Val = 72 : 18**

즉, 최종적으로 Train\:Val\:Test = **72:18:10** 비율로 분할된다.

---

## 데이터프레임 생성

```python
train_df = pd.DataFrame({'filename': train_paths, 'class': train_labels})
val_df = pd.DataFrame({'filename': val_paths, 'class': val_labels})
test_df = pd.DataFrame({'filename': test_paths, 'class': test_labels})
```

이미지 경로와 클래스 라벨을 DataFrame 형태로 저장하여, 이후 `flow_from_dataframe`에서 사용한다.

---

## 이미지 제너레이터

```python
train_datagen = ImageDataGenerator(
    rescale=1./255,
    rotation_range=20,
    width_shift_range=0.1,
    height_shift_range=0.1,
    zoom_range=0.2,
    horizontal_flip=True
)
val_datagen = ImageDataGenerator(rescale=1./255)
test_datagen = ImageDataGenerator(rescale=1./255)
```

* **훈련 데이터**: 이미지 증강(회전, 이동, 줌, 좌우 반전)
* **검증/테스트 데이터**: 단순히 정규화(`rescale=1./255`)만 적용

---

## CNN 모델 정의

```python
model = Sequential([
    Conv2D(32, (3, 3), activation='relu', padding='same', input_shape=(100, 100, 3)),
    MaxPooling2D(2),
    Conv2D(64, (3, 3), activation='relu', padding='same'),
    MaxPooling2D(2),
    Conv2D(128, (3, 3), activation='relu', padding='same'),
    MaxPooling2D(2),
    Flatten(),
    Dense(128, activation='relu'),
    Dropout(0.5),
    Dense(len(class_names), activation='softmax')
])
```

---

# 파라미터 수 계산 핵심 공식

1. **Conv2D 레이어**

   ```
   파라미터 수 = (k_w × k_h × C_in + 1) × C_out
   ```

   * k\_w, k\_h : 커널(필터) 크기
   * C\_in : 입력 채널 수
   * C\_out : 출력 채널(필터 개수)
   * +1 은 bias term

2. **Dense 레이어**

   ```
   파라미터 수 = (N_in + 1) × N_out
   ```

   * N\_in : 입력 뉴런 수
   * N\_out : 출력 뉴런 수
   * +1 은 bias term

3. **Pooling / Flatten / Dropout**

   * 학습 가능한 파라미터 없음

---


# 모델 구조 및 파라미터 계산

```python
model = Sequential([
    Conv2D(32, (3, 3), activation='relu', padding='same', input_shape=(100, 100, 3)),
    MaxPooling2D(2),
    Conv2D(64, (3, 3), activation='relu', padding='same'),
    MaxPooling2D(2),
    Conv2D(128, (3, 3), activation='relu', padding='same'),
    MaxPooling2D(2),
    Flatten(),
    Dense(128, activation='relu'),
    Dropout(0.5),
    Dense(len(class_names), activation='softmax')
])
```
<br/><br/>

---

## 1️⃣ Conv2D(32 filters, 3×3, input\_shape=(100,100,3))

* 입력 채널 **C<sub>in</sub> = 3** (RGB)
* 필터 크기 **3 × 3**
* 필터 개수 **C<sub>out</sub> = 32**

**파라미터 수:** (3 × 3 × 3 + 1) × 32 = (27 + 1) × 32 = **896**
출력 feature map 크기: **(100, 100, 32)**

---

## 2️⃣ MaxPooling2D(2×2)

* 파라미터 없음
* 출력 크기: **(50, 50, 32)**

---

## 3️⃣ Conv2D(64 filters, 3×3)

* 입력 채널 **C<sub>in</sub> = 32**
* 필터 크기 **3 × 3**
* 필터 개수 **C<sub>out</sub> = 64**

**파라미터 수:** (3 × 3 × 32 + 1) × 64 = (288 + 1) × 64 = **18,496**
출력 크기: **(50, 50, 64)**

---

## 4️⃣ MaxPooling2D(2×2)

* 파라미터 없음
* 출력 크기: **(25, 25, 64)**

---

## 5️⃣ Conv2D(128 filters, 3×3)

* 입력 채널 **C<sub>in</sub> = 64**
* 필터 크기 **3 × 3**
* 필터 개수 **C<sub>out</sub> = 128**

**파라미터 수:** (3 × 3 × 64 + 1) × 128 = (576 + 1) × 128 = **73,856**
출력 크기: **(25, 25, 128)**

---

## 6️⃣ MaxPooling2D(2×2)

* 파라미터 없음
* 출력 크기: **(12, 12, 128)**

---

## 7️⃣ Flatten

* **12 × 12 × 128 = 18,432** 노드
* 파라미터 없음

---

## 8️⃣ Dense(128)

* 입력 뉴런: **18,432**
* 출력 뉴런: **128**

**파라미터 수:** (18,432 + 1) × 128 = 18,433 × 128 = **2,359,424**

---

## 9️⃣ Dropout(0.5)

* 파라미터 없음

---

## 🔟 Dense(len(class\_names), softmax)

* 입력 뉴런: **128**
* 출력 뉴런: 클래스 개수 = **N<sub>class</sub>**

**파라미터 수:** (128 + 1) × N<sub>class</sub> = **129 × N<sub>class</sub>**
예: 클래스가 5개라면 **129 × 5 = 645**

---



# 총 파라미터 수 정리

| Layer          | Output Shape   | Params           |
| -------------- | -------------- | ---------------- |
| Conv2D (32)    | (100, 100, 32) | **896**          |
| MaxPooling2D   | (50, 50, 32)   | 0                |
| Conv2D (64)    | (50, 50, 64)   | **18,496**       |
| MaxPooling2D   | (25, 25, 64)   | 0                |
| Conv2D (128)   | (25, 25, 128)  | **73,856**       |
| MaxPooling2D   | (12, 12, 128)  | 0                |
| Flatten        | (18,432)       | 0                |
| Dense (128)    | (128)          | **2,359,424**    |
| Dropout        | (128)          | 0                |
| Dense (Nclass) | (Nclass)       | **129 × Nclass** |

---

따라서 **총 파라미터 수**는


896 + 18,496 + 73,856 + 2,359,424 + (129 \times N_{class})


예를 들어 `N_class = 5`라면


896 + 18,496 + 73,856 + 2,359,424 + 645 = 2,453,317


---

<br/>

## 모델 학습

```python
early_stop = EarlyStopping(monitor='val_loss', patience=5, restore_best_weights=True)
history = model.fit(train_gen, validation_data=val_gen, epochs=30, callbacks=[early_stop])
```

* **EarlyStopping**: 검증 손실이 5번 이상 개선되지 않으면 학습을 조기 종료
* 최적의 가중치를 자동으로 복원

---

## 학습 결과 시각화

```python
plt.plot(history.history['accuracy'], label='Train Accuracy')
plt.plot(history.history['val_accuracy'], label='Validation Accuracy')
plt.xlabel('Epochs')
plt.ylabel('Accuracy')
plt.legend()
plt.title('Training and Validation Accuracy')
plt.grid()
plt.show()
```

* 학습 과정에서 **Train / Validation Accuracy** 변화를 시각적으로 확인

---

## 최종 평가

```python
test_loss, test_acc = model.evaluate(test_gen)
print(f"최종 Test Accuracy: {test_acc:.4f} / 최종 Test Loss: {test_loss:.4f}")
```

* 테스트 데이터셋을 사용하여 최종 성능 측정

---

## 예측 함수

```python
def predict_ripe_class(model, img_path):
    img = image.load_img(img_path, target_size=(100, 100))
    img_array = image.img_to_array(img) / 255.0
    img_array = np.expand_dims(img_array, axis=0)

    predictions = model.predict(img_array)
    class_idx = np.argmax(predictions[0])
    class_labels = class_names
    return class_labels[class_idx], predictions[0]
```

* 개별 이미지 입력 시 **클래스명 + 확률 분포** 반환

---

# 아쉬운 점

* 이미지 크기를 `(100, 100)`으로 줄이면서 세밀한 특징이 손실될 가능성이 있다.
* 단순 CNN 구조이므로 \*\*ResNet, EfficientNet 등 사전학습 모델(Transfer Learning)\*\*을 활용하면 더 높은 정확도를 기대할 수 있다.

---
