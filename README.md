# Golang Logger Package with Zap

This package provides a simple and flexible logging solution for Golang applications using the high-performance [Zap](https://github.com/uber-go/zap) logging library.

## Features

- Environment-based logger configuration
- Support for local, development, staging, and production environments
- JSON logging for non-local environments
- Colored console output for local development

## Installation

```bash
go get github.com/adikhoironhasan/logger
```

## Usage

```go
package main

import (
    "github.com/adikhoironhasan/logger"
    "go.uber.org/zap"
)

func main() {
    // Initialize the logger
    log, err := logger.InitLogger("development")
    if err != nil {
        panic(err)
    }
    defer log.Sync()

    // Use the logger
    log.Info("Application started", zap.String("env", "development"))
}
```

## Environment Configuration

The `InitLogger` function accepts an environment string and configures the logger accordingly:

- `"local"`: Console encoding with colored output, debug level logging
- `"development"`, `"dev"`, `"staging"`, `"stg"`: JSON encoding, debug level logging
- `"production"`, `"prod"`: JSON encoding, info level logging

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.
