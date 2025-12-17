{
  "file_name": "process_log_20251210T150300Z.tar.gz",
  "sha256": "fea62b5c1c7142e744555b45afbcee6ad9b54201fba165ce92957c72766b32fd",
  "signature_file": "process_log.txt.sig",
  "signer": "ABCD EFGH IJKL MNOP QRST UVWX YZ12 3456 7890 ABCD",
  "signer_key_fingerprint": "",
  "signature_method": "PGP/GPG or RSA (مشخص کنید)",
  "signature_verified": null,
  "ipfs_cid": "bafybeib3...",
  "storage": ["USB","CLOUD","IPFS"],
  "storage_locations": {
    "USB": "USB-Label-01 (رمزنگاری‌شده)",
    "CLOUD": "provider://bucket/path/process_log_20251210T150300Z.tar.gz",
    "IPFS_gateway": "https://ipfs.io/ipfs/bafybeib3..."
  },
  "timestamp_utc": "2025-12-10T15:03:00Z",
  "timestamp_token": "",
  "archiver": {
    "name": "",
    "contact": ""
  },
  "status": "ARCHIVED",
  "notes": ""
}
sha256sum process_log_20251210T150300Z.tar.gz
# خروجی را با مقدار ثبت‌شده مقایسه کنید
# فرض: کلید عمومی در pubkey.pem و امضا در process_log.txt.sig
openssl dgst -sha256 -verify pubkey.pem -signature process_log.txt.sig process_log_20251210T150300Z.tar.gz
gpg --import signer_public_key.asc
gpg --verify process_log.txt.sig process_log_20251210T150300Z.tar.gz
ipfs add -Q process_log_20251210T150300Z.tar.gz
# خروجی CID کامل را در مانیفست ثبت کنید
# تولید کوئری تایم‌استمپ
openssl ts -query -data process_log_20251210T150300Z.tar.gz -no_nonce -sha256 -out ts_query.tsq
# ارسال به TSA و دریافت پاسخ (مثال با curl به سرویس TSA)
curl -s --data-binary @ts_query.tsq https://tsa.example.org/tsa -o ts_response.tsr
# اعتبارسنجی پاسخ
openssl ts -reply -in ts_response.tsr -token_out ts_token.der
# اگر qrencode نصب است:
qrencode -o manifest_qr.png "https://example.org/manifest/process_log_manifest.json"
process_log_20251210T150300Z.tar.gz/.🆔سجاد پیرمرادیان:515884163808✅./process_log_20251210T150300Z.tar.gzhttps://ipfs.io/ipfs/bafybeib3pubkey.pemprocess_log.txt.sigsigner_public_key.aschttps://tsa.example.org/tsats_query.tsqts_response.tsrmanifest_qr.pngts_token.derhttps://example.org/manifest/process_log_manifest.json/https://example.org/manifest/process_log_manifest.json/ts_token.der
