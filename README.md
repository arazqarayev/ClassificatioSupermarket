# Classification Supermarket
Lojistik regresyon analizi örneği , Supermarket alış verış deneyimi üzerine


 Müşteri Satın Alma Davranışlarının Analizi

Bu proje, müşteri satın alma davranışlarını analiz etmek için logistic regresyon yöntemini kullanan bir R projesidir. Proje, sosyal ağ reklamları veri seti üzerinde logistic regresyon modeli oluşturmayı ve müşterilerin belirli bir ürünü satın alıp almama olasılığını tahmin etmeyi amaçlar.

## Veri Seti

Kullanılan veri seti, sosyal ağ reklamlarıyla ilgili bilgileri içermektedir. Bu bilgiler arasında kullanıcının yaş, cinsiyet, tahmini maaş gibi demografik özellikleri bulunmaktadır. Ayrıca, kullanıcının bir ürünü satın alıp almadığı da veri setinde yer almaktadır.

## Kullanım

1. R Studio veya benzeri bir R geliştirme ortamında proje klasörünü açıyoruz.
2. Veri setini 'dosya.csv' dosyasından yükleyin.
3. Kodu çalıştırarak logistic regresyon modelini eğitiyoruz.
4. Modelin performansını değerlendirin ve sonuçları yorumluyoruz.

5. dataset <- read.csv('Social_Network_Ads.csv')
dataset <- dataset[3:5]

# Encoding the target feature as factor
dataset$Purchased <- factor(dataset$Purchased, levels = c(0, 1))

# Splitting the dataset into the Training set and Test set
library(caTools)
set.seed(123)
split <- sample.split(dataset$Purchased, SplitRatio = 0.75)
training_set <- subset(dataset, split == TRUE)
test_set <- subset(dataset, split == FALSE)

# Feature Scaling
training_set[, 1:2] <- scale(training_set[, 1:2])
test_set[, 1:2] <- scale(test_set[, 1:2])

# Fitting Logistic Regression to the Training set
classifier <- glm(formula = Purchased ~ .,
                  family = binomial,
                  data = training_set)

# Predicting the Test set results
prob_pred <- predict(classifier, type = 'response', newdata = test_set)
y_pred <- ifelse(prob_pred > 0.5, 1, 0)
dataset <- read.csv('Social_Network_Ads.csv')
dataset <- dataset[3:5]

# Encoding the target feature as factor
dataset$Purchased <- factor(dataset$Purchased, levels = c(0, 1))

# Splitting the dataset into the Training set and Test set
library(caTools)
set.seed(123)
split <- sample.split(dataset$Purchased, SplitRatio = 0.75)
training_set <- subset(dataset, split == TRUE)
test_set <- subset(dataset, split == FALSE)

# Feature Scaling
training_set[, 1:2] <- scale(training_set[, 1:2])
test_set[, 1:2] <- scale(test_set[, 1:2])

# Fitting Logistic Regression to the Training set
classifier <- glm(formula = Purchased ~ .,
                  family = binomial,
                  data = training_set)

# Predicting the Test set results
prob_pred <- predict(classifier, type = 'response', newdata = test_set)
y_pred <- ifelse(prob_pred > 0.5, 1, 0)
cm
cm
   y_pred
     0  1
  0 57  7
  1 10 26
> 57+26
>  83
> 100 kisiden 83 kisi dogru prognoz verilmis
