# Đồ án cuối kỳ Máy học – Nhóm 06: phần việc của Huỳnh Tấn Lộc

- **Sinh viên:** Huỳnh Tấn Lộc – MSSV 3124411158 – lớp DCT124C1, Trường Đại học Sài Gòn
- **Đề tài nhóm:** Product Classification and Clustering (PriceRunner, UCI #837): phân loại 35.311 tiêu đề sản phẩm vào 10 ngành và phân cụm
- **Repo nhóm (bản đầy đủ, chạy được):** https://github.com/Huynh-Quoc-Danh/mayhoc (thư mục `DoAnCuoiKy`, nhánh làm việc của mình là `loc`)
- **Thành viên:** Huỳnh Quốc Danh (nhóm trưởng), Huỳnh Tấn Lộc, Mai Tấn Thiện Nhân, Nguyễn Vĩnh Thịnh

Thư mục này chỉ chứa những file **mình làm** trong repo nhóm, chép lại từ 17 commit của mình (11 pull request đã merge vào main). Mỗi commit ở đây ứng với đúng một commit trong repo nhóm, ghi ngày làm, nội dung và link về commit gốc. Code chung (`src/`, dữ liệu) nằm ở repo nhóm, nên muốn chạy lại thì làm theo README của repo nhóm.

## Phần việc được giao

| Phần | Nội dung |
|---|---|
| Thí nghiệm | Naive Bayes (Multinomial, Complement) và Logistic Regression trên TF-IDF – notebook 04 |
| Báo cáo | Chương 2 (Dữ liệu và EDA), Chương 3 (Tiền xử lý và đặc trưng), mục 4.1 (NB, LR) |
| Slide | Slide 3–5: Dữ liệu, EDA, Tiền xử lý |
| Kiểm tra trước khi nộp | Chạy lại từ bản clone mới, cập nhật README của nhóm |
| Đọc chéo | Góp ý Chương 6 (So sánh mô hình và phân tích lỗi) của Nhân |

## Kết quả chính

| Mô hình (TF-IDF từ (1,2) + n-gram ký tự (2,4)) | Test Macro-F1 | CV 5-fold | Group split | run_id |
|---|---|---|---|---|
| Logistic Regression, C=100 | 0.9909 | 0.9875 ± 0.0016 | 0.9851 | loc_20261114_175918 (chạy lại loc_20261120_210027) |
| MultinomialNB, alpha=0.03 | 0.9869 | 0.9861 ± 0.0014 | 0.9819 | loc_20261114_175845 (chạy lại loc_20261120_210139) |
| ComplementNB, alpha=0.03 | 0.9857 | – | – | loc_20261115_142042 |

So với giữa kỳ (NB 0.9663), thêm n-gram ký tự giúp NB/LR tăng khoảng 2 điểm. Mô hình cuối của nhóm là SVM tuyến tính của Danh (0.9929); LR đứng thứ hai và được dùng để giải thích đặc trưng.

## Nhật ký theo ngày

| Ngày | Công việc | Commit nhóm | PR |
|---|---|---|---|
| 12/11/2026 | Cài môi trường, tái lập E01 NB (F1 0.9663); thử alpha=1.0 và ngram (1,1) | [9bbe9b9](https://github.com/Huynh-Quoc-Danh/mayhoc/commit/9bbe9b9) | #7 |
| 12/11/2026 | Notebook 04 mục 1: kiểm chứng số liệu EDA, nhận xét `clean_title`; xuất HTML | [b2baed2](https://github.com/Huynh-Quoc-Danh/mayhoc/commit/b2baed2), [e52cbbb](https://github.com/Huynh-Quoc-Danh/mayhoc/commit/e52cbbb) | #11 |
| 12/11/2026 | Notebook 04 mục 2–7: quét ngram, min_df, alpha, C; NB min_df=1 alpha=0.01 đạt 0.980 | [b465b9f](https://github.com/Huynh-Quoc-Danh/mayhoc/commit/b465b9f) | #11 |
| 13/11/2026 | Giải thích EDA; ComplementNB; NB/LR thêm n-gram ký tự (LR 0.9890, NB 0.9851) | [d2ba1a0](https://github.com/Huynh-Quoc-Danh/mayhoc/commit/d2ba1a0) | #16 |
| 14/11/2026 | Quét alpha, C với n-gram ký tự (2,4); CV 5-fold NB 0.9861, LR 0.9875; hình so sánh tuyến tính | [1a0c313](https://github.com/Huynh-Quoc-Danh/mayhoc/commit/1a0c313) | #28 |
| 15/11/2026 | LR class_weight balanced, ComplementNB, Group split theo Cluster ID; sơ đồ tiền xử lý vẽ tay | [05bddf8](https://github.com/Huynh-Quoc-Danh/mayhoc/commit/05bddf8) | #33 |
| 16/11/2026 | Giải thích LR: 8 đặc trưng mạnh nhất mỗi ngành; họp nhóm 1 | [61fa83e](https://github.com/Huynh-Quoc-Danh/mayhoc/commit/61fa83e) | #41 |
| 17/11/2026 | Tổng kết notebook 04 (mục 11); viết báo cáo Ch.2, Ch.3, mục 4.1 | [bce68b2](https://github.com/Huynh-Quoc-Danh/mayhoc/commit/bce68b2) | #46 |
| 18/11/2026 | Rà soát báo cáo, xuất lại Hình 2.5, góp ý Ch.6 (14 bình luận), phác slide dữ liệu, script vẽ draw.io | [f9c90a9](https://github.com/Huynh-Quoc-Danh/mayhoc/commit/f9c90a9), [0d8bcf3](https://github.com/Huynh-Quoc-Danh/mayhoc/commit/0d8bcf3), [3972c52](https://github.com/Huynh-Quoc-Danh/mayhoc/commit/3972c52), [df26c74](https://github.com/Huynh-Quoc-Danh/mayhoc/commit/df26c74) | #55 |
| 19/11/2026 | Dán Ch.2, Ch.3, mục 4.1 lên báo cáo chung trên Google Docs; nhật ký | [8245b95](https://github.com/Huynh-Quoc-Danh/mayhoc/commit/8245b95), [1c5558b](https://github.com/Huynh-Quoc-Danh/mayhoc/commit/1c5558b) | #65 |
| 20/11/2026 | Chạy lại LR và NB với thư mục kết quả đầy đủ (khớp run 14/11); slide 3–5 | [495cb5c](https://github.com/Huynh-Quoc-Danh/mayhoc/commit/495cb5c) | #67 |
| 21/11/2026 | Chạy lại từ bản clone mới trên Mac (SVM 0.9929, K-Means NMI 0.7318); cập nhật README nhóm; bình luận Ch.6 trên Docs | [d45d516](https://github.com/Huynh-Quoc-Danh/mayhoc/commit/d45d516) | #73 |

Chi tiết từng ngày (run_id, nhận xét) nằm trong `experiments/loc/nhat_ky.md`.

## Cấu trúc thư mục

```
notebooks/04_Loc_TienXuLy_NB_LR.ipynb   notebook thí nghiệm NB/LR (mục 1–11)
experiments/loc/nhat_ky.md              nhật ký làm việc từng ngày
experiments/loc/experiment_log.csv      bảng tất cả các run, có nhận xét
experiments/loc/runs/                   kết quả từng run (.json), thư mục đầy đủ của 2 run 20/11, bản HTML notebook theo ngày
figures/loc_*.png                       hình: alpha/C, so sánh mô hình tuyến tính, đặc trưng quan trọng
docs/hinh_ve_tay/loc_so_do_tien_xu_ly.jpg  sơ đồ tiền xử lý vẽ tay
scripts/loc_ve_drawio.py                script vẽ Hình 2.3–2.4 của báo cáo
report/nhap/BaoCao_Loc.docx             bản nháp Ch.2, Ch.3, mục 4.1
report/nhap/GopY_Loc_cho_Ch6.docx       góp ý Chương 6 của Nhân
report/nhap/Slide_Loc_nhap.docx         phác thảo slide
report/slide/Slide_Loc.pptx             slide 3–5
```

Phần README chung của nhóm mà mình cập nhật ngày 21/11 xem tại https://github.com/Huynh-Quoc-Danh/mayhoc/blob/main/DoAnCuoiKy/README.md
