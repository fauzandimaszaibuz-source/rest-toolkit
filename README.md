# rest-toolkit

[![Build Status](https://img.shields.io/github/actions/workflow/status/user/rest-toolkit/ci.yml?branch=main)]()
[![Go Version](https://img.shields.io/badge/go-1.22+-blue.svg)]()
[![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)

Opinionated REST API toolkit with validation, pagination, and error handling — designed for production workloads with a focus on reliability and developer ergonomics.

## Features

- **Zero Dependencies** — No external packages required for core functionality
- **Context Support** — Full context.Context propagation for cancellation and deadlines
- **Graceful Shutdown** — Clean shutdown handling with configurable drain timeout
- **Minimal Allocations** — Designed to minimize GC pressure in hot paths

## Installation

```bash
go get github.com/user/rest-toolkit@latest
```

## Usage

```go
package main

import (
	"fmt"
	"github.com/user/rest-toolkit"
)

func main() {
	client := resttoolkit.New(
		resttoolkit.WithTimeout(30 * time.Second),
	)

	result, err := client.Run(context.Background())
	if err != nil {
		log.Fatal(err)
	}

	fmt.Println(result)
}
```

## Configuration

Configuration can be provided via environment variables, a config file, or programmatically.

| Variable | Description | Default |
|----------|-------------|--------|
| `REST_TOOLKIT_TIMEOUT` | Request timeout in seconds | `30` |
| `REST_TOOLKIT_RETRIES` | Number of retry attempts | `3` |
| `REST_TOOLKIT_LOG_LEVEL` | Log verbosity (debug, info, warn, error) | `info` |

## License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.
