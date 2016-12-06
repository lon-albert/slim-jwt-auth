# PSR-7 JWT Authentication Middleware

## This is a fork from [slim-jwt-auth](https://github.com/tuupola/slim-jwt-auth)

### Error

Error is called when authentication fails. It receives last error message in arguments.
It is the only function that is currently changed

```php
$app = new \Slim\App();

$app->add(new \Slim\Middleware\JwtAuthentication([
    "secret" => "supersecretkeyyoushouldnotcommittogithub",
    "error" => function ($request, $response, $next, $arguments) {
        $data["status"] = "error";
        $data["message"] = $arguments["message"];
        return $response
            ->withHeader("Content-Type", "application/json")
            ->write(json_encode($data, JSON_UNESCAPED_SLASHES | JSON_PRETTY_PRINT));
    }
]));
```