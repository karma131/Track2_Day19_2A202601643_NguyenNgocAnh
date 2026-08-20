# Reflection — Lab 19

**Tên:** Nguyễn Ngọc Anh
**Cohort:** AI20-K3
**Path đã chạy:** lite

---

## Câu hỏi (≤ 200 chữ)

> Trên golden set 50 queries, mode nào thắng ở loại query nào (`exact` /
> `paraphrase` / `mixed`), và tại sao? Khi nào bạn **không** dùng hybrid
> (i.e. khi nào pure BM25 hoặc pure vector là lựa chọn đúng)?

Trên golden set 50 truy vấn, hybrid RRF đạt Precision@10 trung bình 78,6%,
cao hơn BM25 (77,8%) và vector (73,2%). Với truy vấn `exact`, BM25 và hybrid
cùng đạt 96,7% vì các thuật ngữ xuất hiện nguyên văn. Với `mixed`, hybrid đạt
100%, tốt hơn BM25 (97,0%) và vector (98,5%), do RRF kết hợp được tín hiệu từ
khớp từ khóa lẫn tương đồng ngữ nghĩa. Trên `paraphrase`, cả ba mode đều yếu;
BM25 đạt 33,3%, hybrid 32,0% và vector 24,0%. Nguyên nhân chính là model
`bge-small-en-v1.5` thiên về tiếng Anh nên biểu diễn câu diễn đạt lại bằng tiếng
Việt chưa tốt; đây là trường hợp nên thử `bge-m3` rồi index lại.

Tôi không dùng hybrid khi truy vấn là mã, tên riêng hoặc thuật ngữ cần khớp
chính xác (BM25 đơn giản, nhanh hơn), hoặc khi người dùng diễn đạt hoàn toàn
theo ngữ nghĩa và đã có model embedding đa ngôn ngữ tốt (vector phù hợp hơn).

---

## Điều ngạc nhiên nhất khi làm lab này

Hybrid không tự động thắng mọi lát cắt: chất lượng embedding và ngôn ngữ của
corpus quyết định rất lớn đến hiệu quả của phần semantic.

---

## Bonus challenge

- [ ] Đã làm bonus (xem `bonus/`)
- [x] Làm cá nhân
