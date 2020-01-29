+++
title = "My Journey"
outputs = ["Reveal"]
+++

# My Journey on Elixir

Lenfree Yeung

---

# About Me

- operations and automation
- used to call DevOps but it is not really a role, rather a culture
- new fancy name SRE
- Ruby - first programming language I love
- started Golang - when Vagrant and Docker came out and it was shiny the new thing at that time
- tried Haskell but too difficult to understand because of my small brain
- tried Elixir and love it

---

# How I got started with Elixir

- word of mouth
- first Elixir application
  - had to migrate and own old application design while maintaining backwards compatibility
    - parse logs and return a CSV output while keeping history from Elasticsearch and an existing file
    - wrote this in Go but found edge cases such as new version came out while older data doesn't have them.
      Hence, I have to find a dynamic language to easily handle them
    - didn't pick Ruby because it was an opportunity to learn Elixir
    - had to implement own sort function and it wasn't hard
    - it was easy for my teammate with to collaborate

---

# Things I like

- syntax feels like home
- community
- easy to find solutions/answers from Google search
- helped me understand how map and other enum
  functions are implemented - when I was writing in Ruby, I only know
  how to use them
- supervisor
- liveview
- OTP is similar to Golang channel

---

# Things I dislike

- roles are hard to find
- a bit of a challege to get a real world experience

---

# Rate limiter

Repo: https://github.com/lenfree/rate_limiting

A library that stops a particular requestor from
making too many http requests within a particular
period of time. After the limit has been reached,
return a 429 with the text "Rate limit exceeded.
Try again in #{n}
seconds".

---

# Solution

- ETS
- Supervisor
- GenServer

---

#

```elixir
%RateLimiting.Config{
    time_request_made: DateTime.utc_now(),
    count: 0,
    interval_seconds: @interval_seconds,
    max_requests_count: @max_requests_count,
    duration_in_seconds: 0,
    source_ip_address: source_ip_address,
    valid: true
}
```

- Check if particular source exists in table:
  - if so, get information and compare the following:
    - duration_in_seconds > interval_seconds
  - if not, add entry to table

---

# Demo

---

# Learnings

- get right data structure
- struct keys should have had better names
- should have used Redis or equivalent rather than ETS when client > 1
- I will still choose Elixir over other languages
