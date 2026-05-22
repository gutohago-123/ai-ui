FROM golang:1.26-bookworm

# تثبيت مكتبات النظام المطلوبة للـ FFI والتشفير
RUN apt-get update && apt-get install -y --no-install-recommends \
    libffi-dev \
    gcc \
    libc6-dev \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app

# نسخ ملفات الباك إند
COPY . .

# إعداد بيئة Go والبناء
ENV CGO_ENABLED=1
ENV GOTOOLCHAIN=auto
RUN go build -o main ./cmd/main.go

# قراءة المنفذ تلقائياً من Render
EXPOSE 10000
CMD ["./main"]
