# ML/DL Master Concept Table

**Source:** Andrew Ng — Machine Learning Specialization + Deep Learning Specialization  
**Total:** 60 concepts · 6 layers  
**Format:** Layer | Concept | Vietnamese | Requires | Unlocks

---

## Tầng 0 — ML Foundations (9 concepts)

| Concept                             | Vietnamese                            | Requires                                                   | Unlocks                                                                                         |
| ----------------------------------- | ------------------------------------- | ---------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| Supervised vs Unsupervised Learning | Học có / không giám sát               | —                                                          | [[Linear Regression]], [[Logistic Regression]], [[Clustering (K-Means)]], [[Anomaly Detection]] |
| Linear Regression                   | Hồi quy tuyến tính                    | [[Supervised vs Unsupervised Learning]]                    | [[Cost Function]], [[Gradient Descent]], [[Overfitting / Underfitting]]                         |
| Logistic Regression                 | Hồi quy logistic                      | [[Linear Regression]], [[Cost Function]]                   | [[Sigmoid vs Softmax]], [[Loss Function]], [[Binary Classification]]                            |
| Cost Function                       | Hàm chi phí (MSE, Cross-entropy)      | [[Linear Regression]]                                      | [[Gradient Descent]], [[Loss Function]], [[Backpropagation]]                                    |
| Train / Dev / Test Split            | Tập huấn luyện / kiểm định / kiểm tra | [[Supervised vs Unsupervised Learning]]                    | [[Overfitting / Underfitting]], [[Bias-Variance Tradeoff]], [[Error Analysis]]                  |
| Feature Engineering                 | Kỹ thuật đặc trưng                    | [[Supervised vs Unsupervised Learning]]                    | [[Overfitting / Underfitting]], [[Data Augmentation]]                                           |
| Decision Tree / Random Forest       | Cây quyết định / Rừng ngẫu nhiên      | [[Supervised vs Unsupervised Learning]], [[Cost Function]] | [[Bias-Variance Tradeoff]], [[Hyperparameter Tuning]]                                           |
| Clustering (K-Means)                | Phân cụm                              | [[Supervised vs Unsupervised Learning]]                    | [[Anomaly Detection]]                                                                           |
| Anomaly Detection                   | Phát hiện bất thường                  | [[Clustering (K-Means)]], [[Cost Function]]                | [[Error Analysis]]                                                                              |

---

## Tầng 1 — Foundations (9 concepts)

|Concept|Vietnamese|Requires|Unlocks|
|---|---|---|---|
|Neural Network|Mạng nơ-ron nhân tạo|[[Supervised vs Unsupervised Learning]], [[Logistic Regression]]|[[Neuron / Node]], [[Forward Propagation]], [[Backpropagation]]|
|Neuron / Node|Nút / Nơ-ron|[[Neural Network]]|[[Weight & Bias]], [[Activation Function]]|
|Weight & Bias|Trọng số & Hệ số chệch|[[Neuron / Node]]|[[Forward Propagation]], [[Gradient Descent]], [[Xavier / He Initialization]]|
|Activation Function|Hàm kích hoạt (ReLU, Sigmoid, Tanh)|[[Neuron / Node]], [[Weight & Bias]]|[[Sigmoid vs Softmax]], [[Vanishing / Exploding Gradient]], [[Forward Propagation]]|
|Sigmoid vs Softmax|Binary vs multi-class output|[[Activation Function]], [[Logistic Regression]]|[[Loss Function]], [[Accuracy]], [[Confusion Matrix]]|
|Loss Function|Hàm mất mát|[[Cost Function]], [[Sigmoid vs Softmax]]|[[Gradient Descent]], [[Backpropagation]], [[Overfitting / Underfitting]]|
|Gradient Descent|Hạ dốc gradient|[[Loss Function]], [[Cost Function]]|[[Learning Rate]], [[Backpropagation]], [[Momentum]], [[Adam Optimizer]]|
|Vectorization|Vector hóa — tránh for-loop|[[Neural Network]], [[Weight & Bias]]|[[Forward Propagation]], [[Batch / Mini-batch / Epoch]]|
|Xavier / He Initialization|Khởi tạo tham số|[[Weight & Bias]], [[Activation Function]]|[[Vanishing / Exploding Gradient]], [[Backpropagation]]|

---

## Tầng 2 — Core Mechanisms (13 concepts)

|Concept|Vietnamese|Requires|Unlocks|
|---|---|---|---|
|Forward Propagation|Lan truyền xuôi|[[Neural Network]], [[Weight & Bias]], [[Activation Function]], [[Vectorization]]|[[Backpropagation]], [[Loss Function]]|
|Backpropagation|Lan truyền ngược|[[Forward Propagation]], [[Loss Function]], [[Cost Function]], [[Xavier / He Initialization]]|[[Gradient Descent]], [[Vanishing / Exploding Gradient]], [[Gradient Checking]]|
|Learning Rate|Tốc độ học|[[Gradient Descent]]|[[Momentum]], [[RMSprop]], [[Adam Optimizer]], [[Learning Rate Decay]]|
|Overfitting / Underfitting|Khớp quá / Khớp thiếu|[[Train / Dev / Test Split]], [[Loss Function]], [[Feature Engineering]]|[[Regularization (L1/L2, Dropout)]], [[Bias-Variance Tradeoff]], [[Data Augmentation]]|
|Regularization (L1/L2, Dropout)|Chính quy hóa|[[Overfitting / Underfitting]], [[Weight & Bias]]|[[Batch Normalization]], [[Bias-Variance Tradeoff]]|
|Batch / Mini-batch / Epoch|Lô dữ liệu / Vòng lặp|[[Gradient Descent]], [[Vectorization]]|[[Batch Normalization]], [[Momentum]], [[Adam Optimizer]]|
|Batch Normalization|Chuẩn hóa theo lô|[[Batch / Mini-batch / Epoch]], [[Regularization (L1/L2, Dropout)]]|[[Vanishing / Exploding Gradient]], [[Hyperparameter Tuning]]|
|Momentum|Động lượng trong tối ưu hóa|[[Gradient Descent]], [[Learning Rate]], [[Batch / Mini-batch / Epoch]]|[[Adam Optimizer]]|
|RMSprop|Thuật toán tối ưu thích nghi|[[Gradient Descent]], [[Learning Rate]]|[[Adam Optimizer]]|
|Adam Optimizer|Kết hợp Momentum + RMSprop|[[Momentum]], [[RMSprop]], [[Learning Rate]]|[[Hyperparameter Tuning]], [[Learning Rate Decay]]|
|Vanishing / Exploding Gradient|Gradient tiêu biến / bùng nổ|[[Backpropagation]], [[Activation Function]], [[Xavier / He Initialization]], [[Batch Normalization]]|[[LSTM / GRU]], [[ResNet]]|
|Learning Rate Decay|Giảm tốc độ học theo thời gian|[[Learning Rate]], [[Adam Optimizer]]|[[Hyperparameter Tuning]]|
|Gradient Checking|Kiểm tra gradient|[[Backpropagation]], [[Cost Function]]|[[Hyperparameter Tuning]]|

---

## Tầng 3 — Architectures (12 concepts)

|Concept|Vietnamese|Requires|Unlocks|
|---|---|---|---|
|CNN|Mạng tích chập|[[Neural Network]], [[Forward Propagation]], [[Backpropagation]], [[Activation Function]]|[[ResNet]], [[Inception Network]], [[Object Detection / YOLO]], [[Transfer Learning]]|
|ResNet|Mạng phần dư — skip connections|[[CNN]], [[Vanishing / Exploding Gradient]]|[[Transfer Learning]], [[Fine-tuning]]|
|Inception Network|Kiến trúc song song multi-scale|[[CNN]], [[Hyperparameter Tuning]]|[[Transfer Learning]]|
|Object Detection / YOLO|Nhận diện đối tượng|[[CNN]], [[Loss Function]]|[[Transfer Learning]]|
|RNN|Mạng hồi quy|[[Neural Network]], [[Forward Propagation]], [[Backpropagation]]|[[LSTM / GRU]], [[Vanishing / Exploding Gradient]]|
|LSTM / GRU|Bộ nhớ dài-ngắn hạn|[[RNN]], [[Vanishing / Exploding Gradient]]|[[Attention Mechanism]], [[Beam Search]]|
|Attention Mechanism|Cơ chế chú ý|[[LSTM / GRU]], [[Embeddings]]|[[Multi-head Attention]], [[Transformer]]|
|Multi-head Attention|Chú ý đa đầu|[[Attention Mechanism]]|[[Transformer]]|
|Transformer|Bộ biến đổi|[[Multi-head Attention]], [[Embeddings]], [[Batch Normalization]]|[[Transfer Learning]], [[Fine-tuning]]|
|Embeddings|Biểu diễn nhúng|[[Word2Vec / GloVe]], [[Neural Network]]|[[Attention Mechanism]], [[Transformer]]|
|Word2Vec / GloVe|Biểu diễn từ dạng vector|[[Supervised vs Unsupervised Learning]], [[Neural Network]]|[[Embeddings]]|
|Beam Search|Tìm kiếm chùm — seq2seq|[[LSTM / GRU]], [[Logistic Regression]]|[[Error Analysis]]|

---

## Tầng 4 — Advanced & Strategy (9 concepts)

|Concept|Vietnamese|Requires|Unlocks|
|---|---|---|---|
|Transfer Learning|Học chuyển tiếp|[[CNN]] hoặc [[Transformer]], [[Fine-tuning]]|[[Multi-task Learning]], [[Data Augmentation]]|
|Fine-tuning|Tinh chỉnh mô hình|[[Transfer Learning]], [[Hyperparameter Tuning]]|[[Multi-task Learning]]|
|Bias-Variance Tradeoff|Đánh đổi độ lệch - phương sai|[[Overfitting / Underfitting]], [[Train / Dev / Test Split]], [[Decision Tree / Random Forest]]|[[Error Analysis]], [[Hyperparameter Tuning]], [[Mismatched Train/Test Distribution]]|
|Hyperparameter Tuning|Điều chỉnh siêu tham số|[[Adam Optimizer]], [[Batch Normalization]], [[Learning Rate Decay]], [[Gradient Checking]]|[[Fine-tuning]], [[Error Analysis]]|
|Error Analysis|Phân tích lỗi|[[Bias-Variance Tradeoff]], [[Train / Dev / Test Split]], [[Confusion Matrix]], [[Beam Search]]|[[Mismatched Train/Test Distribution]], [[Data Augmentation]]|
|Data Augmentation|Tăng cường dữ liệu|[[Overfitting / Underfitting]], [[Feature Engineering]], [[Transfer Learning]]|[[Error Analysis]]|
|Human-level Performance / Bayes Error|Hiệu suất người / sai số Bayes|[[Bias-Variance Tradeoff]], [[Train / Dev / Test Split]]|[[Error Analysis]], [[Mismatched Train/Test Distribution]]|
|Mismatched Train/Test Distribution|Phân phối dữ liệu không khớp|[[Train / Dev / Test Split]], [[Bias-Variance Tradeoff]], [[Human-level Performance / Bayes Error]]|[[Error Analysis]]|
|Multi-task Learning|Học đa nhiệm|[[Transfer Learning]], [[Fine-tuning]], [[Loss Function]]|—|

---

## Evaluation Metrics (8 concepts)

|Concept|Vietnamese|Requires|Unlocks|
|---|---|---|---|
|Accuracy|Độ chính xác tổng thể|[[Sigmoid vs Softmax]], [[Train / Dev / Test Split]]|[[Confusion Matrix]], [[Bias-Variance Tradeoff]]|
|Precision|Độ chính xác dương tính|[[Confusion Matrix]]|[[F1 Score]], [[Satisficing vs Optimizing Metric]]|
|Recall (Sensitivity)|Độ nhạy|[[Confusion Matrix]]|[[F1 Score]], [[Satisficing vs Optimizing Metric]]|
|F1 Score|Trung bình điều hòa Precision & Recall|[[Precision]], [[Recall (Sensitivity)]]|[[Satisficing vs Optimizing Metric]], [[Single Number Evaluation]]|
|AUC-ROC|Diện tích dưới đường ROC|[[Accuracy]], [[Confusion Matrix]]|[[Satisficing vs Optimizing Metric]]|
|Confusion Matrix|Ma trận nhầm lẫn|[[Accuracy]], [[Sigmoid vs Softmax]]|[[Precision]], [[Recall (Sensitivity)]], [[AUC-ROC]], [[Error Analysis]]|
|Satisficing vs Optimizing Metric|Chỉ số thỏa mãn / tối ưu|[[F1 Score]], [[AUC-ROC]]|[[Single Number Evaluation]]|
|Single Number Evaluation|Chỉ số đơn trên tập dev|[[Satisficing vs Optimizing Metric]], [[F1 Score]]|[[Error Analysis]], [[Hyperparameter Tuning]]|