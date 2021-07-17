# 常见问题

## waitFor系列函数全部不可用

> #### danger:: `waitFor`系列的所有函数都无效
> 经过实际测试，`waitFor`系列的各个函数，此处都无效
```python
    # await page.waitForSelector(SearchFoundWordsSelector)
    # await page.waitFor(SearchFoundWordsSelector)
    # await page.waitForXPath(SearchFoundWordsXpath)
    # Note: all above exception: 发生异常: ElementHandleError Evaluation failed: TypeError: MutationObserver is not a constructor
```
> 都会报错：`ElementHandleError Evaluation failed: TypeError: MutationObserver is not a constructor`

所以，如果想要实现，等待元素出现，只能`while`+`querySelector`去不断检测去实现

比如

```python
waitSeconds = 1
while not await page.querySelector(xxxSelector):
  await asyncio.sleep(waitSeconds)
```
