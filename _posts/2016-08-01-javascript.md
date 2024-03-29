---
layout: post
title: javascript
---
{{ page.title }}
================

# IIFE Immediately Invoked Function Expression 即时执行函数 自执行匿名函数 

IIFE 即时执行函数
```javascript
(function () {
  /* ... */
})();
```

Arrow function IIFE 表达式即时执行函数
```javascript
(() => {
  /* ... */
})();

```

async IIFE 异步即时执行函数
```javascript
(async () => {
  /* ... */
})();

```




[Immediately Invoked Function Expression](https://developer.mozilla.org/en-US/docs/Glossary/IIFE)

# js file md5 前端分片计算文件md5值 

参照：[md5-hash-a-large-file-incrementally](https://stackoverflow.com/a/38432807)

```js
function calculateMD5Hash(file, bufferSize) {
  var def = Q.defer();

  var fileReader = new FileReader();
  var fileSlicer = File.prototype.slice || File.prototype.mozSlice || File.prototype.webkitSlice;
  var hashAlgorithm = new SparkMD5();
  var totalParts = Math.ceil(file.size / bufferSize);
  var currentPart = 0;
  var startTime = new Date().getTime();

  fileReader.onload = function(e) {
    currentPart += 1;

    def.notify({
      currentPart: currentPart,
      totalParts: totalParts
    });

    var buffer = e.target.result;
    hashAlgorithm.appendBinary(buffer);

    if (currentPart < totalParts) {
      processNextPart();
      return;
    }

    def.resolve({
      hashResult: hashAlgorithm.end(),
      duration: new Date().getTime() - startTime
    });
  };

  fileReader.onerror = function(e) {
    def.reject(e);
  };

  function processNextPart() {
    var start = currentPart * bufferSize;
    var end = Math.min(start + bufferSize, file.size);
    fileReader.readAsBinaryString(fileSlicer.call(file, start, end));
  }

  processNextPart();
  return def.promise;
}

function calculate() {

  var input = document.getElementById('file');
  if (!input.files.length) {
    return;
  }

  var file = input.files[0];
  var bufferSize = Math.pow(1024, 2) * 10; // 10MB

  calculateMD5Hash(file, bufferSize).then(
    function(result) {
      // Success
      console.log(result);
    },
    function(err) {
      // There was an error,
    },
    function(progress) {
      // We get notified of the progress as it is executed
      console.log(progress.currentPart, 'of', progress.totalParts, 'Total bytes:', progress.currentPart * bufferSize, 'of', progress.totalParts * bufferSize);
    });
}
```

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/q.js/1.4.1/q.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/spark-md5/2.0.2/spark-md5.min.js"></script>


<div>
  <input type="file" id="file"/>
  <input type="button" onclick="calculate();" value="Calculate" class="btn primary" />
</div>
```

# 局部变量全局变量的问题

参考stackoverflow上的一个回答

[What is the scope of variables in JavaScript?](http://stackoverflow.com/questions/500431/what-is-the-scope-of-variables-in-javascript)

