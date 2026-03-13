# 08 — S3

## Overview

Object storage API over HTTP; similar to REST + binary blobs and auth (signing or SDK). Use MinIO or real S3.

**Why this order:** Object storage API (HTTP); similar to REST + binary blobs and auth (signing or SDK).

**Minimal spec:** Upload (PUT) and download (GET) an object to/from a bucket; use MinIO or S3.

---

## Per-language notes

| Language   | Notes |
| ---------- | ----- |
| **Python** | boto3. |
| **JavaScript** | @aws-sdk/client-s3 or minio package. |
| **Go** | aws-sdk-go-v2 or minio-go. |
| **Java** | AWS SDK for Java or MinIO Java. |
| **Rust** | aws-sdk-s3 or rusoto_s3. |
| **Zig** | MinIO C SDK or custom signing + HTTP. |
| **C++** | AWS SDK C++ or minio-c. |
| **C** | libcurl + custom signing or minio-c. |
