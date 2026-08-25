---
layout: home
title: Pro Collaboration Controller
---

![Pro Collaboration Controller logo](logo.png)

**Pro Collaboration Controller** coordinates a user's own subscription ChatGPT
Pro chats for long research, mathematical reasoning, planning, review, and
independent critique.

它把用户自己的订阅版 ChatGPT Pro 对话作为可复用计算资源。Controller 负责锁定根
目标、给不同角色传递最少必要上下文、记录实际返回结果，并在对话过长前生成可恢复交接。

## What it does

- routes bounded tasks across planning, solving, critique, and acceptance roles;
- compresses accepted context instead of repeatedly sending the full history;
- records observable model and result identity without inventing unavailable evidence;
- avoids wasteful high-frequency polling;
- stops when Pro is unavailable unless the user explicitly authorizes a named fallback;
- labels every authorized non-Pro or API result as non-Pro and records its model,
  cost, and data boundary where observable.

The plugin does not include a ChatGPT Pro subscription. It does not promise a
fixed token-saving percentage, a particular model route, or correct research
results. Important outputs must be reviewed before use.

This is an independently developed third-party plugin. It is not made,
supported, certified, or endorsed by OpenAI. ChatGPT, Codex, OpenAI, and related
marks belong to their respective owners.

## Public documents

- [Privacy notice](privacy.html)
- [End user terms](terms.html)
- [Support](support.html)
- [Personal and Evaluation License 1.0](license.txt)

Publisher: **knockknock-hoho**

