# Telegram bot API Client written in Golang

[![Travis](https://travis-ci.org/devalecs/tgo.svg)](https://travis-ci.org/devalecs/tgo)
[![GoDoc](https://godoc.org/github.com/devalecs/tgo?status.svg)](https://godoc.org/github.com/devalecs/tgo)

**GetUpdatesChan example**
```go
package main

import "gopkg.in/devalecs/tgo.v1"

func main() {
	c := tgo.NewClient("yourTelegramBotAPIToken")

	updatesChan := c.GetUpdatesChan(tgo.GetUpdatesParams{
		Timeout: 60,
	})

	for update := range updatesChan {
		if update.Message == nil {
			continue
		}

		c.SendMessage(tgo.SendMessageParams{
			ChatID: update.Message.Chat.ID,
			Text:   "Pong",
		})
	}
}
```
