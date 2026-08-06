---
title: "AWS Elastic Beanstalk 업로드 최대 크기 512MB"
date: 2023-08-25
categories:
 - Memo
naver_url: https://blog.naver.com/rage147-owo/223193323918
---

ERROR: FileTooLargeError - Archive cannot be any larger than 512MB

AWS Elastic Beanstalk에서 한번의 업로드 최대 크기는 512MB이다.(zip으로 묶어서..)

용량이 큰 파일은 S3를 사용하거나 ec2로 올리자...