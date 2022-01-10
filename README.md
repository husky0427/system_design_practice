# system_design_practice

## 2. 停車場金流



## 3. 停車場資訊更新
1. 假設停車場資訊, 是由政府提供公開api取得, 且更新頻率為每1分鐘更新1次: 
2. 利用 redis 做 cache, 有效時間設定為1分鐘, 若 query 的停車場或區域為同一個地區, 則先從cache中取得資訊, 若cache中無資訊, 則透過政府提供api取得資訊, 並更新cache資訊
3. Web Server 和 AP Server 數量需視 QPS 而定, 但為奇數台, 可另外用 health-check 機制檢查機器是否存活, 可避免單點失效
4. 使用雲端的 solution 與否, 首先看需求量而定, 若為業務初期, 租用雲端serverless 服務, 成本較低, 且可主動做到auto-scaling及load balance(如 AWS 的 ELB 和 auto-scaling group)
