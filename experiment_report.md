# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** 2A202600129
**Name:** Ngô Văn Long
**Date:** 2026-04-15

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | "The best choice is Laptop at $1200." | 9 | Dung san pham, gia chinh xac, category sach |
| Garbage Data (`garbage_data.csv`) | "The best choice is Nuclear Reactor at $999999." | 1 | Agent chon outlier cuc doan, hoan toan sai lech voi thuc te |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Khi su dung garbage_data.csv, Agent tra loi sai vi bo du lieu chua nhieu van de nghiem trong ve chat luong.

Thu nhat, co Extreme Outlier: san pham "Nuclear Reactor" co gia 999999 USD - mot gia tri phi thuc te - khien Agent chon no la "best deal" vi logic tim max price. Du lieu sach da loc bo cac gia tri nay truoc khi dua vao mo hinh.

Thu hai, co Duplicate IDs: ID so 1 xuat hien hai lan (Laptop va Banana), gay ra su nham lan ve du lieu, lam mat tinh nhat quan cua dataset.

Thu ba, co Wrong Data Types: san pham "Broken Chair" co gia la chuoi "ten dollars" thay vi so, co the gay ra loi khi Agent co xu ly gia tri so.

Thu tu, co Null Values: ban ghi "Ghost Item" co ID va category la None, co the khien Agent bi loi hoac suy luan sai.

Ket luan: garbage data khong chi gay ra ket qua sai ma con lam mat tin cay toan bo he thong. Agent chi tot bang chat luong du lieu no su dung - "Garbage In, Garbage Out" la nguyen tac co ban trong data engineering.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** Dong y hoan toan.

Du co prompt tot den dau, neu du lieu dau vao co van de (outlier, null, wrong type, duplicate), ket qua cua Agent van se sai. Trong thu nghiem nay, cung mot cau hoi va cung mot logic Agent, nhung garbage data cho ket qua hoan toan sai lech (Nuclear Reactor $999,999 thay vi Laptop $1,200). Data quality la nen tang, prompt chi la cong cu tren nen tang do.
