---
title: jmeter
---

- Number of JSON Path variables must match number of default values and json-path expressions,check you use separator ';' if you have many values.
	- ![2021_03_02_image.png](https://cdn.logseq.com/%2F72223880-dff3-4195-b002-58f583924ddd2bb83f2e-8c77-48d7-a69c-ba8a72ff45542021_03_02_image.png?Expires=4768273157&Signature=k-hi~kgmJdY0IYXz~ynRSCEmNIbPFsvqGTTw9ce7kIvw9gr3Nfq5AF11ZtxVmVkLf92Q97Xx9hhjvTCgkA1ysT9I-EMFLWUWuBVwXKq090LDQg-wRJztPSqmyA8iWr15d9rnTL-juPdxa-chnSgHStWfbhfKyrI8bWhjasupbf2EjzqWkTpek1RiY3SfjljgrGdCWY6KPJ~2joYvVuzpxRVpgeSYvrjWxwxNvlWsbUSX0Jwq~ztSnQlWHHOf4oaF4HsTWG6RH4lApKGkiRsGYVjxk9-Htb6YImcAO9JE5gaPu7MppwCK5~TOpUmVbzRU8uR1xW-ydPFtZmiuqadWlg__&Key-Pair-Id=APKAJE5CCD6X7MP6PTEA)
- 不同线程组的HTTP采样器，不能共享变量
	- 如setUp线程组的`HTTP采样器`，使用`JSON提取器`，返回变量值。 普通线程组发起请求，不能识别该变量的值
- 选项-日志查看，日志级别
- 调试采样器， 线程组-new-sampler-debug sampler