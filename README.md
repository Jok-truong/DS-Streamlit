# Breast Cancer Predictor (DS-Streamlit)

Một ứng dụng Streamlit giúp dự đoán u vú (benign/malignant) dựa trên các đặc trưng hình thái của tế bào (cell nuclei measurements). Ứng dụng sử dụng một mô hình machine-learning (được huấn luyện trước) để dự đoán xác suất khối u là lành tính hay ác tính dựa trên dữ liệu đo từ mẫu mô.

---

## 📌 Mục tiêu dự án

- Truyền dữ liệu đo các đặc trưng tế bào vào một mô hình huấn luyện sẵn để dự đoán khối u vú (Benign hoặc Malignant).
- Tạo giao diện người dùng (UI) bằng Streamlit cho phép: chỉnh giá trị thông số bằng slider, trực quan hoá biểu đồ radar (radar chart) so sánh Mean / SE / Worst values, và hiện kết quả dự đoán cùng xác suất.

---

## 🌟 Nội dung chính của repo

- `app/` — chứa mã Source cho Streamlit app và notebook: `app.py`, `app.ipynb`.
- `data/` — dữ liệu thô: `data.csv` (Breast cancer dataset).
- `model/` — tệp mô hình đã huấn luyện và scaler (`model.pkl`, `scaler.pkl`) và notebook huấn luyện: `breast_cancer_diagnois_model.ipynb`.
- `assets/` — chứa file CSS phục vụ giao diện: `style.css`.
- `requirements.txt` — danh sách các packages cần cài đặt.

---

## ⚙️ Cài đặt & chạy ứng dụng (Local)

1. Clone repo và chuyển vào thư mục project:

```bash
git clone <repo-url>
cd breast_cancer_diagnois
```

2. Tạo virtual environment và cài dependencies (Python >= 3.9 recommended):

```bash
python -m venv .venv
source .venv/Scripts/activate      # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

3. Chạy Streamlit app:

```bash
streamlit run app/app.py
```

Lưu ý: app sử dụng đường dẫn tương đối tới `../data/data.csv` và `../model/model.pkl` / `../model/scaler.pkl`. Hãy chắc rằng bạn chạy lệnh từ root project (thư mục chứa `app/`, `data/`, `model/`).

---

## 🧠 Mô tả app

- `app.py` cung cấp giao diện Streamlit gồm:
  - Sidebar chứa các slider cho 30 chỉ số tế bào (mean, se, worst của 10 features), cho phép người dùng nhập hoặc điều chỉnh các giá trị.
  - Biểu đồ radar (Plotly) so sánh 3 tập giá trị (mean, standard error, worst) dựa trên input hiện tại.
  - Khu vực kết quả dự đoán: hiển thị nhãn (Benign / Malicious) và xác suất dự đoán.

---

## 📁 Chi tiết dữ liệu & mô hình

- Dữ liệu: `data/data.csv` là dataset chuẩn (Breast Cancer Wisconsin Dataset) đã được làm sạch (`id` và `Unnamed: 32` bị loại bỏ).
- Mô hình: `model/model.pkl` (model huấn luyện — classifier, ví dụ RandomForest/Logistic), `model/scaler.pkl` (StandardScaler hoặc tương tự) để chuẩn hoá input trước khi dự đoán.
