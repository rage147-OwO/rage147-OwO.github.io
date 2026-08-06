---
title: "fastapi Too many fields, Too many files Error"
date: 2024-02-18
categories:
 - Memo
naver_url: https://blog.naver.com/rage147-owo/223356916948
---

fastapi에서 파일이나 필드가 1000개를 넘어갈 때가 있다

기본값이 1000이기에 넘어가면 에러가 아래와 같이 나온다

Too many fields. Maximum number of fields is 1000

Too many files. Maximum number of files is 1000

주의할 점은 fastapi가 아닌 starlette 라이브러리에서 제한을 풀어줘야 한다

```
#site-packages-starlette-formparsers.py

import sys
class MultiPartParser:
    max_file_size = 1024 * 1024

    def __init__(
        self,
        headers: Headers,
        stream: typing.AsyncGenerator[bytes, None],
        *,
        max_files: typing.Union[int, float] = sys.maxsize, #64bit에서 최대 9223372036854775807
        max_fields: typing.Union[int, float] = sys.maxsize,
    ) -> None:
```