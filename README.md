# Cargo-BOJ

Test and submit solutions to BOJ (Baekjoon Online Judge) problems.

Defaults are geared towards Rust solutions, but non-Rust usage is supported as well.

## Prerequisites

A stable Rust toolchain.

## Installation

```
cargo install cargo-boj
```

## Usage

The default usage of `test` and `submit` commands assume that `cargo boj` is being run at the crate root with
either `src/main.rs` or `src/bin/main.rs` being the solution file.

### Login

Logging in to BOJ with ID and password cannot be automated because it is protected with reCaptcha.
So, the users are expected to log in on their own browser first, and then copy relevant cookies into `cargo-boj`.

```
$ cargo boj login
First log in to www.acmicpc.net on your browser with auto-login enabled.
Then copy and paste two cookies for www.acmicpc.net from your browser.
bojautologin: 3b1adXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
OnlineJudge: n00lXXXXXXXXXXXXXXXXXXXXXX
Cookies set.
```

or:

```
$ cargo boj login --bojautologin=3b1adXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX --onlinejudge=n00lXXXXXXXXXXXXXXXXXXXXXX
```

### Test

Tests your code against example test cases for the given problem.

* Test cases are fetched once and then cached.
* A colored diff is provided when a test fails with Wrong Answer.

```
# Test main.rs against example test cases of problem 1000
$ cargo boj test 1000
# Test sol_1000.rs
$ cargo boj test 1000 --bin=sol_1000
# Test 1000.py
$ cargo boj test 1000 --cmd='python 1000.py'
```

### Submit

Submits your code to BOJ using the credentials provided with `cargo boj login`.

The default language is `Rust 2021` (language ID 113). To submit solutions in other languages,
refer to [BOJ Help: language info](https://help.acmicpc.net/language/info).

```
# Submit main.rs as Rust 2021 solution to problem 1000. Code open setting follows account preference
$ cargo boj submit 1000
# Submit sol_1000.rs as Rust 2018 solution, with code closed
$ cargo boj submit 1000 --path=src/bin/sol_1000.rs --lang=94 --code-open=n
```
