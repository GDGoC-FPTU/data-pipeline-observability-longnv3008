[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23572382&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** longnv3008@gmail.com
**Student ID:** 2A202600129
**Name:** Ngô Văn Long

---

## Mo ta

Bai lab xay dung mot ETL Pipeline tu dong doc du lieu tu file JSON, kiem tra chat luong du lieu (validation), chuan hoa (transform) va luu ra file CSV. Sau do chay Agent Simulation voi du lieu sach va du lieu "rac" de chung minh tam quan trong cua Data Quality trong he thong AI.

Pipeline thuc hien 4 buoc chinh:
1. **Extract**: Doc file `raw_data.json`
2. **Validate**: Loai bo record co `price <= 0` hoac `category` rong
3. **Transform**: Tinh `discounted_price = price * 0.9`, chuan hoa category thanh Title Case, them timestamp `processed_at`
4. **Load**: Luu ket qua ra `processed_data.csv`

---

## Cach chay (How to Run)

### Prerequisites
```bash
pip install pandas
```

### Chay ETL Pipeline
```bash
python solution.py
```

### Chay Agent Simulation (Stress Test)
```bash
# Buoc 1: Tao garbage data
python generate_garbage.py

# Buoc 2: Chay agent voi ca 2 bo du lieu
python agent_simulation.py
```

---

## Cau truc thu muc

```
├── solution.py              # ETL Pipeline script
├── processed_data.csv       # Output cua pipeline (Clean Data)
├── garbage_data.csv         # Du lieu "rac" de stress test
├── raw_data.json            # Du lieu dau vao goc
├── agent_simulation.py      # Agent simulation script
├── generate_garbage.py      # Script tao garbage data
├── experiment_report.md     # Bao cao thi nghiem
└── README.md                # File nay
```

---

## Ket qua

- **Tong records doc vao**: 5
- **Records hop le (kept)**: 3 (Laptop, Chair, Monitor)
- **Records bi loai (dropped)**: 2
  - Mystery Box: price = -10 (am)
  - Phone: category rong

- **Agent voi Clean Data**: Chon dung "Laptop at $1200" (accurate)
- **Agent voi Garbage Data**: Chon sai "Nuclear Reactor at $999,999" (outlier)
