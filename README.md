# **1. Tên đề tài**

Xây dựng Chatbot hỗ trợ tư vấn pháp luật lao động và bảo hiểm xã hội cho người dân Việt Nam.

# **2. Lý do chọn đề tài**

Pháp luật lao động và bảo hiểm xã hội liên quan trực tiếp đến quyền lợi của người lao động. Tuy nhiên, thông tin pháp luật được phân bố trên nhiều luật, nghị định, thông tư và văn bản hướng dẫn. Người không chuyên về pháp luật thường khó xác định văn bản nào phù hợp với tình huống cụ thể, điều khoản nào cần đọc và văn bản đó còn hiệu lực hay không.

Đề tài kết hợp LLM với Retrieval-Augmented Generation (RAG). Thay vì để mô hình tự trả lời hoàn toàn dựa trên kiến thức đã học, hệ thống tìm kiếm các đoạn văn bản pháp luật liên quan từ kho dữ liệu được quản lý, sau đó cung cấp chúng làm ngữ cảnh cho LLM. Cách tiếp cận này phù hợp với bài toán pháp luật vì yêu cầu cao về căn cứ, khả năng kiểm chứng và cập nhật dữ liệu.

Đề tài đồng thời có tính ứng dụng và có chiều sâu kỹ thuật đối với hướng Data/AI: thu thập và chuẩn hóa dữ liệu, NLP, embedding, semantic search, vector database, RAG, prompt engineering, đánh giá mô hình và xây dựng ứng dụng web.

# **3. Mục tiêu đề tài**

## **3.1. Mục tiêu tổng quát**

Xây dựng một hệ thống chatbot hỗ trợ người lao động Việt Nam tra cứu, tìm hiểu và giải thích các quy định về pháp luật lao động và bảo hiểm xã hội bằng ngôn ngữ tự nhiên; đồng thời cung cấp căn cứ hoặc nguồn văn bản liên quan để người dùng có thể kiểm chứng.

## **3.2. Mục tiêu cụ thể**

* Xây dựng kho dữ liệu pháp luật lao động và bảo hiểm xã hội từ các nguồn chính thống.
* Chuẩn hóa dữ liệu và giữ cấu trúc văn bản như chương, điều, khoản, điểm.
* Gắn metadata về số hiệu, cơ quan ban hành, ngày ban hành, ngày hiệu lực và trạng thái hiệu lực.
* Xây dựng tìm kiếm ngữ nghĩa để tìm các đoạn quy định liên quan đến câu hỏi.
* Triển khai pipeline RAG kết hợp retrieval và LLM.
* Cho phép chatbot hỏi bổ sung khi câu hỏi còn thiếu dữ kiện quan trọng.
* Hiển thị căn cứ pháp lý và nguồn văn bản khi có thể xác định.
* Đánh giá hệ thống theo độ chính xác truy xuất, độ chính xác câu trả lời, độ chính xác căn cứ và nguy cơ hallucination.

# **4. Phạm vi đề tài**

## **4.1. Phạm vi nội dung**

Phạm vi tập trung vào hai nhóm chính. Nhóm thứ nhất là pháp luật lao động; nhóm thứ hai là bảo hiểm xã hội. Đề tài không đặt mục tiêu bao phủ toàn bộ hệ thống pháp luật Việt Nam.

Các chủ đề pháp luật lao động dự kiến:

* Hợp đồng lao động và thử việc.
* Tiền lương.
* Thời giờ làm việc, thời giờ nghỉ ngơi và làm thêm giờ.
* Nghỉ phép, nghỉ lễ.
* Kỷ luật lao động.
* Chấm dứt hợp đồng lao động.
* Một số quyền và nghĩa vụ cơ bản của người lao động.

Các chủ đề bảo hiểm xã hội dự kiến:

* BHXH bắt buộc và BHXH tự nguyện.
* Một số vấn đề về tham gia, đóng BHXH.
* Chế độ ốm đau.
* Chế độ thai sản.
* Chế độ hưu trí.
* Chế độ tử tuất.
* Bảo hiểm thất nghiệp có thể được bổ sung như phần mở rộng nếu thời gian và dữ liệu cho phép.

Không đưa thuế vào phạm vi cốt lõi. Các nội dung như tư vấn tranh tụng, đại diện pháp lý hoặc thay thế luật sư cũng không thuộc phạm vi của hệ thống.

## **4.2. Phạm vi người dùng**

Đối tượng chính là người lao động Việt Nam có nhu cầu tra cứu và hiểu các quy định cơ bản. Có thể mở rộng cho sinh viên, nhân sự doanh nghiệp hoặc người sử dụng lao động ở giai đoạn sau.

# **5. Hướng triển khai**

Hướng triển khai đề xuất là kiến trúc RAG, trong đó kho văn bản pháp luật được quản lý như nguồn tri thức trung tâm. LLM làm nhiệm vụ hiểu câu hỏi, tổng hợp và diễn đạt câu trả lời dựa trên những đoạn văn bản được truy xuất.

## **5.1. Xây dựng kho dữ liệu**

1. Thu thập văn bản từ các nguồn chính thống.
2. Làm sạch và chuẩn hóa định dạng.
3. Tách văn bản theo Điều/Khoản/Điểm hoặc đoạn nội dung có ý nghĩa.
4. Gắn metadata phục vụ lọc theo lĩnh vực và hiệu lực.
5. Tạo embedding cho các đoạn văn bản.
6. Lưu vector và metadata vào vector database.

## **5.2. Xây dựng pipeline hỏi đáp**

1. Nhận câu hỏi từ người dùng.
2. Phân tích ý định và chủ đề.
3. Kiểm tra dữ kiện còn thiếu.
4. Tạo embedding cho câu hỏi.
5. Tìm kiếm các đoạn pháp luật liên quan.
6. Lọc/xếp hạng kết quả và ưu tiên văn bản phù hợp, còn hiệu lực.
7. Đưa câu hỏi và các đoạn nguồn vào LLM.
8. Tạo câu trả lời có giải thích, căn cứ và lưu ý.
9. Nếu không đủ căn cứ thì trả lời theo hướng giới hạn phạm vi thay vì tự suy đoán.

# **6. Nguyên lý vận hành tổng quát**

Luồng vận hành tổng quát:

**Người dùng → Giao diện Chatbot → Phân tích câu hỏi → Semantic Search → Vector Database/Kho văn bản → Lọc và xếp hạng nguồn → LLM → Câu trả lời + căn cứ pháp lý → Người dùng.**

Ví dụ, người dùng hỏi:

> “Tôi nghỉ việc thì cần báo trước bao lâu?”

Hệ thống trước hết nhận diện chủ đề là chấm dứt hợp đồng lao động. Nếu câu hỏi thiếu thông tin ảnh hưởng đến kết quả, chatbot có thể hỏi thêm về loại hợp đồng hoặc trường hợp cụ thể. Sau đó hệ thống truy xuất các điều khoản liên quan từ kho văn bản, đưa các đoạn này vào LLM và yêu cầu mô hình giải thích dễ hiểu, đồng thời chỉ ra nguồn được sử dụng.

# **7. Kiến trúc hệ thống dự kiến**

* **Presentation Layer:** giao diện web/chat.
* **Conversation Layer:** phiên hội thoại, lịch sử và câu hỏi bổ sung.
* **NLP/LLM Layer:** embedding, prompt, LLM và xử lý ngôn ngữ.
* **Retrieval Layer:** semantic search, metadata filtering, reranking.
* **Knowledge Layer:** văn bản pháp luật, metadata và vector database.
* **Administration Layer:** cập nhật dữ liệu, quản trị văn bản và kiểm tra trạng thái.

Kiến trúc có thể mở rộng theo hướng:

**Người dùng → API Backend → Conversation Manager → Retrieval Service → Knowledge Base → LLM Service → Response Validator → Giao diện.**

# **8. Công nghệ sử dụng**

| Thành phần    | Công nghệ đề xuất                        | Vai trò                                   |
| ------------- | ---------------------------------------- | ----------------------------------------- |
| Ngôn ngữ      | Python                                   | Xử lý dữ liệu, NLP, RAG và backend        |
| Backend       | FastAPI                                  | Xây dựng API cho chatbot                  |
| LLM           | LLM API hoặc mô hình phù hợp             | Sinh và giải thích câu trả lời            |
| Embedding     | Sentence Transformers hoặc embedding API | Biểu diễn văn bản và câu hỏi thành vector |
| Vector DB     | FAISS / Chroma / Qdrant                  | Lưu trữ và tìm kiếm embedding             |
| RAG           | LangChain hoặc LlamaIndex                | Điều phối retrieval và generation         |
| Cơ sở dữ liệu | PostgreSQL                               | Người dùng, phiên chat, metadata          |
| Frontend      | React hoặc Streamlit                     | Giao diện chatbot                         |
| Đóng gói      | Docker                                   | Môi trường triển khai                     |
| Đánh giá      | Python + bộ câu hỏi kiểm thử             | Đo chất lượng retrieval và answer         |

# **9. Nhược điểm và giới hạn**

* Không thay thế luật sư hoặc cơ quan có thẩm quyền.
* Phụ thuộc vào chất lượng và độ cập nhật của kho dữ liệu.
* LLM vẫn có thể hallucination nếu retrieval hoặc prompt không tốt.
* Một số trường hợp cần nhiều dữ kiện thực tế và không thể kết luận chỉ từ một câu hỏi ngắn.
* Văn bản pháp luật có thể được sửa đổi, bổ sung hoặc thay thế.
* API LLM hoặc tài nguyên tính toán có thể phát sinh chi phí.

# **10. Khó khăn dự kiến và hướng giải quyết**

| Khó khăn         | Nguyên nhân                              | Hướng giải quyết                                                       |
| ---------------- | ---------------------------------------- | ---------------------------------------------------------------------- |
| Thu thập dữ liệu | Nhiều văn bản, nhiều định dạng           | Ưu tiên nguồn chính thống, chuẩn hóa và gắn metadata.                  |
| Văn bản thay đổi | Có văn bản sửa đổi/thay thế/hết hiệu lực | Lưu ngày hiệu lực, trạng thái và phiên bản; kiểm tra cập nhật định kỳ. |
| Truy xuất sai    | Câu hỏi dùng ngôn ngữ đời thường         | Embedding + semantic search + metadata filtering + reranking.          |
| Hallucination    | LLM có thể tự suy diễn                   | RAG + prompt ràng buộc + yêu cầu căn cứ + kiểm thử hallucination.      |
| Thiếu dữ kiện    | Quy định phụ thuộc tình huống            | Thiết kế cơ chế hỏi bổ sung.                                           |
| Tính toán        | Có công thức/điều kiện pháp lý           | Ưu tiên code/rule engine cho phép tính và kiểm tra điều kiện.          |
| Đánh giá         | Pháp luật có nhiều trường hợp ngoại lệ   | Xây bộ câu hỏi có đáp án chuẩn, chấm retrieval và answer riêng.        |
| Chi phí          | LLM API và hạ tầng                       | Cache, giới hạn token, mô hình phù hợp và có thể thử local model.      |

# **11. Tổ chức dữ liệu pháp luật**

Mỗi đoạn văn bản nên được lưu cùng metadata để phục vụ truy xuất, kiểm tra hiệu lực và hiển thị căn cứ. Một cấu trúc tham khảo:

```text
document_id | tên văn bản | số hiệu | cơ quan ban hành | ngày ban hành |
ngày hiệu lực | trạng thái | lĩnh vực | chương | điều | khoản | điểm | nội dung
```

Việc giữ cấu trúc Điều/Khoản/Điểm giúp hệ thống không chỉ tìm được đoạn văn bản mà còn xác định được vị trí pháp lý để hiển thị cho người dùng.

Đặc biệt, trạng thái hiệu lực cần được xem là một thuộc tính dữ liệu quan trọng. Khi ingest hoặc cập nhật dữ liệu, hệ thống cần kiểm tra ngày hiệu lực và các văn bản sửa đổi/thay thế để hạn chế việc truy xuất quy định đã không còn phù hợp.

# **12. Chức năng dự kiến**

* Chat hỏi đáp bằng ngôn ngữ tự nhiên.
* Câu trả lời gồm: kết luận sơ bộ → giải thích → căn cứ pháp lý → lưu ý.
* Hiển thị nguồn và điều/khoản liên quan.
* Hỏi bổ sung khi câu hỏi chưa đủ dữ kiện.
* Tìm kiếm văn bản pháp luật.
* Quản trị và cập nhật kho dữ liệu.
* Theo dõi lịch sử hội thoại.
* Một số công cụ kiểm tra/tính toán ở phạm vi được chọn.

# **13. Phương pháp đánh giá**

* **Retrieval Accuracy:** đoạn được truy xuất có chứa căn cứ cần thiết hay không.
* **Answer Correctness:** câu trả lời có phù hợp với đáp án chuẩn hay không.
* **Citation Correctness:** căn cứ được dẫn có đúng với kết luận hay không.
* **Relevance:** câu trả lời có trực tiếp giải quyết câu hỏi không.
* **Hallucination Rate:** tỷ lệ nội dung không có căn cứ trong dữ liệu nguồn.
* **Latency:** thời gian phản hồi trung bình.
* **User Satisfaction:** mức độ dễ hiểu, hữu ích và tin cậy.

# **14. Kế hoạch triển khai dự kiến**

* **Giai đoạn 1:** Khảo sát bài toán, xác định phạm vi và bộ câu hỏi kiểm thử.
* **Giai đoạn 2:** Thu thập, chuẩn hóa và gắn metadata cho dữ liệu.
* **Giai đoạn 3:** Xây dựng embedding và vector database.
* **Giai đoạn 4:** Xây dựng và đánh giá retrieval/RAG.
* **Giai đoạn 5:** Tích hợp LLM, prompt và cơ chế trích dẫn.
* **Giai đoạn 6:** Xây dựng frontend và quản trị dữ liệu.
* **Giai đoạn 7:** Bổ sung hội thoại nhiều lượt và công cụ tính toán.
* **Giai đoạn 8:** Kiểm thử, đánh giá, tối ưu và hoàn thiện báo cáo.

# **15. Nguồn tài liệu tham khảo chính thống**

Do đây là đề tài về pháp luật, nguồn dữ liệu nên ưu tiên văn bản gốc và cổng thông tin của cơ quan nhà nước có thẩm quyền. Tại thời điểm xây dựng báo cáo, các nguồn quan trọng gồm:

* **Cổng Thông tin điện tử Chính phủ – Bộ luật Lao động số 45/2019/QH14.**
  https://vanban.chinhphu.vn/?classid=1&docid=198540&pageid=27160&typegroupid=3

* **Cổng Thông tin điện tử Chính phủ – Luật Bảo hiểm xã hội số 41/2024/QH15.**
  https://vanban.chinhphu.vn/?docid=211199&pageid=27160

* **Cổng Thông tin điện tử Bảo hiểm xã hội Việt Nam – Hệ thống văn bản quy phạm pháp luật.**
  https://baohiemxahoi.gov.vn/vanban/Pages/default.aspx

* **Bảo hiểm xã hội Việt Nam – Trang thông tin về Luật Bảo hiểm xã hội năm 2024.**
  https://baohiemxahoi.gov.vn/vanban/Pages/default.aspx?ItemID=4973

Lưu ý: hệ thống không nên chỉ “chụp” dữ liệu một lần. Vì pháp luật có thể thay đổi, quy trình cập nhật dữ liệu phải là một phần của thiết kế hệ thống. Cổng BHXH Việt Nam hiện cung cấp danh mục văn bản và thông tin ngày ban hành/ngày hiệu lực/trạng thái cho nhiều văn bản, phù hợp làm nguồn kiểm tra và cập nhật metadata.

### **Tài liệu và dự án tham khảo**

* **Legal Question Answering System using Knowledge Graphs and Neural Retrieval**
  https://github.com/nmhieuhieuhieu/LegalChatbotVN_UETThesis

  Một khóa luận tốt nghiệp xây dựng chatbot hỏi đáp pháp luật Việt Nam. Hệ thống kết hợp Knowledge Graph, Hybrid Retrieval, BM25, BGE-M3, Reranking và RAG, và còn có bước kiểm tra/xử lý nhiều tầng trước khi sinh câu trả lời.

* **Vietnamese Legal Retrieval Dataset**
  https://github.com/Tsurasu/legal_retrieval

  Đây là dataset tập trung riêng vào truy xuất văn bản pháp luật tiếng Việt. Nó rất phù hợp để tham khảo cho phần đánh giá khả năng tìm đúng điều luật của chatbot.

* **Vietnamese Legal Instruction Dataset**
  https://github.com/duyet/vietnamese-legal-documents-dataset

  Ý tưởng để xây bộ câu hỏi kiểm thử chatbot, thay vì chỉ tự nghĩ vài chục câu hỏi.

* **ViLegalText – Corpus pháp luật tiếng Việt**
  https://huggingface.co/datasets/ntphuc149/ViLegalText

  ViLegalText là corpus được dùng để huấn luyện ViLegalLM, được tạo từ nhiều nguồn văn bản pháp luật công khai.
