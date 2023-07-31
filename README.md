# 安装

```
composer require ledc/macroable
```



# 使用

```
<?php

use Ledc\Macroable\Macro;
use Ledc\Macroable\Macroable;

require_once __DIR__ . '/vendor/autoload.php';
class Tests
{
    //use Macroable;
    use Macro;
}

class Request
{
    //use Macroable;
    use Macro;
}

$ts = new Tests();
$ts->macro('hello', function () {
    echo 'hello Tests' . PHP_EOL;
});
$ts->hello();

$req = new Request();
$req->macro('hello', function () {
    echo 'hello Request' . PHP_EOL;
});
$req->hello();
```



# 最佳实践

- 宏指令方法不存在状态，无上下文依赖时：用`Ledc\Macroable\Macroable`
- 宏指令方法存在状态或依赖上下文时，用：`Ledc\Macroable\Macro`



# 使用场景

| 特性trait                  | 使用场景                                          |
| -------------------------- | ------------------------------------------------- |
| `Ledc\Macroable\Macroable` | PHP-FPM，或宏指令方法无状态                       |
| `Ledc\Macroable\Macro`     | PHP-CLI，中间件内对请求对象注入方法(请求结束销毁) |

