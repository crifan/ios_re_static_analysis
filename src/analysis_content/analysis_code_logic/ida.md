# IDA

TODO：

* 【记录】IDA分析脱壳后抖音ipa的二进制AwemeCore

* 【已解决】iOS底层函数：objc_enumerationMutation
* 【未解决】研究抖音越狱检测逻辑：___lldb_unnamed_symbol1841884即sub_11326A84

---

后已整理出独立教程，详见：

[逆向利器：IDA (crifan.org)](https://book.crifan.org/books/reverse_tool_ida/website/)

## iOS逆向之IDA使用心得

### objc_enumerationMutation表示循环的逻辑

iOS逆向期间，IDA的伪代码中，有时候会看到：`objc_enumerationMutation`

其含义是：`只是表示这段代码是循环遍历而已`

代码举例：

```c
  v4 = (void *)objc_retain(v2->_allTrackRenderers);
  v5 = v4;
  v6 = objc_msgSend(v4, "countByEnumeratingWithState:objects:count:", &v24, &v28, 16LL);
  if ( v6 )
  {
    v7 = v6;
    v8 = *(_QWORD *)v25;
    do
    {
      v9 = 0LL;
      do
      {
        if ( *(_QWORD *)v25 != v8 )
          objc_enumerationMutation(v5);
        objc_msgSend(*(void **)(*((_QWORD *)&v24 + 1) + 8 * v9++), "terminate");
      }
      while ( v9 < (unsigned __int64)v7 );
      v7 = objc_msgSend(v5, "countByEnumeratingWithState:objects:count:", &v24, &v28, 16LL);
    }
    while ( v7 );
  }
```

和：

```c
    do
    {
      v34 = 0LL;
...
      v81 = v31;
      do
      {
        if ( *(_QWORD *)v98 != v32 )
          objc_enumerationMutation(v28);
        v86 = v34;
        v35 = *(_QWORD *)(*((_QWORD *)&v97 + 1) + 8 * v34);
        v85 = jmp_objc_msgSend_x19tox2(v26[83], objectForKeyedSubscript__);
...
      }
      while ( v86 + 1 < (unsigned __int64)v31 );
      v31 = objc_msgSend(v28, v73, &v97, &v109, 16LL);
    }
    while ( v31 );
```
