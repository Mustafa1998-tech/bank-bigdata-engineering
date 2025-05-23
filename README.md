
# bank-data

## مشروع هندسة البيانات الضخمة لبنك - Big Data Engineering for Bank

### الوصف
هذا المشروع هو نظام كامل لمعالجة بيانات معاملات بنكية ضخمة باستخدام Apache Kafka، Apache Spark، وMinIO (كخادم تخزين S3 متوافق).

يقوم المشروع بـ:
- توليد بيانات معاملات بنكية عشوائية وإرسالها إلى Kafka.
- استقبال البيانات ومعالجتها باستخدام Spark Streaming.
- تخزين البيانات المعالجة في MinIO بصيغة Parquet.
- استعلام وتحليل البيانات لكشف المعاملات المشبوهة.

---

### المتطلبات

- Java 8 أو أحدث
- Apache Kafka
- Apache Spark (مع دعم Kafka)
- MinIO (كخادم تخزين S3)
- Python 3
- مكتبات Python: kafka-python, pyspark

---

### طريقة التشغيل

#### 1. تشغيل MinIO

\`\`\`bash
minio server ~/minio/data --console-address ":9001"
\`\`\`

#### 2. إعداد Kafka وتشغيله

- شغل ZooKeeper و Kafka
- أنشئ موضوع \`bank-transactions\`:

\`\`\`bash
kafka-topics.sh --create --topic bank-transactions --bootstrap-server localhost:9092
\`\`\`

#### 3. تشغيل سكربت توليد البيانات (Producer)

\`\`\`bash
python3 producer.py
\`\`\`

#### 4. تشغيل سكربت معالجة البيانات بـ Spark Streaming

\`\`\`bash
spark-submit spark_streaming.py
\`\`\`

#### 5. استعلام وتحليل البيانات

\`\`\`bash
spark-submit analyze_data.py
\`\`\`

---

### ملفات المشروع

- \`producer.py\` : سكربت توليد البيانات وإرسالها لكافكا.
- \`spark_streaming.py\` : سكربت استقبال البيانات من كافكا وتخزينها في MinIO.
- \`analyze_data.py\` : سكربت استعلام وتحليل البيانات.

---

### ملاحظات

- تأكد من إعداد MinIO و Kafka بشكل صحيح.
- مفاتيح الدخول لـ MinIO في السكربت هي \`admin\` و \`admin123\`.
- يمكنك تعديل إعدادات الاتصال حسب بيئتك.

---

### روابط مفيدة

- [MinIO Documentation](https://docs.min.io)
- [Apache Kafka Documentation](https://kafka.apache.org/documentation/)
- [Apache Spark Streaming](https://spark.apache.org/docs/latest/streaming-programming-guide.html)

---

### ترخيص

هذا المشروع مفتوح المصدر تحت رخصة GNU AGPLv3.

---

>>>>>>> 1222667 (Initial commit - bank big data engineering project)
