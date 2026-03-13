# 08 — S3 / Object Storage

## Overview

Store and retrieve binary objects using an S3-compatible API. The baseline uses MinIO so every language can target the same local service instead of relying on cloud-specific setup.

**Why this order:** It introduces binary payloads and external object storage while staying close to familiar HTTP concepts.

## Required contract

- Use a MinIO-compatible endpoint for the baseline implementation.
- Read configuration from environment variables:
  - `S3_ENDPOINT`
  - `S3_BUCKET`
  - `S3_ACCESS_KEY`
  - `S3_SECRET_KEY`
- Expose:
  - `PUT /objects/{key}` to upload the raw request body
  - `GET /objects/{key}` to download the same bytes
- Return `201` after a successful upload and `200` with the stored bytes on download.

## Acceptance checks

- Uploading a small text payload to `PUT /objects/hello.txt` returns `201`.
- Downloading `GET /objects/hello.txt` returns `200` and the same bytes.
- Re-running the app against the same MinIO bucket still allows the object to be read.

## Failure cases

- Reading a missing object returns `404`.
- Missing required S3 configuration fails clearly at startup.
- The baseline should not require custom request signing by hand.

## Extensions

- Generate presigned URLs.
- Add object metadata.
- Support real AWS S3 after the MinIO baseline works.

## Per-language notes

| Language   | Notes |
| ---------- | ----- |
| **Python** | Recommended: `boto3`. |
| **JavaScript** | Recommended: `@aws-sdk/client-s3` or the MinIO client. |
| **Go** | Recommended: `aws-sdk-go-v2` or `minio-go`. |
| **Java** | Recommended: AWS SDK for Java or MinIO Java. |
| **Rust** | Recommended: `aws-sdk-s3`. |
| **Zig** | Prefer MinIO-compatible C bindings or a thin SDK path over manual signing. |
| **C++** | Prefer AWS SDK C++ or MinIO bindings. |
| **C** | Prefer MinIO-compatible bindings over raw `libcurl` plus custom signing. |
