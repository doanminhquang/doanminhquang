name: main

on:
  # Cho phép chạy bằng tay từ giao diện Github
  workflow_dispatch:
  # Lên lịch chạy hàng ngày vào lúc 00:00 UTC
  schedule:
  - cron: "0 0 * * *"

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v2
    - uses: actions/setup-node@v1
      # Khởi tạo môi trường NodeJS
      with:
        node-version: 12.16.1
    - run: npm ci
    - name: Generate quote
      # Chạy script để gọi API lấy quote sau đó sửa file README.md
      run: npm run generate
    - name: Update README.md
      # Push file README.md đã được thay đổi lên github
      run: |
        git config --global user.email "john@example.com"
        git config --global user.name "example"
        git add .
        git commit -m "Updated README.md" || echo "No changes to commit"
        git push
