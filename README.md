[🇺🇸 English](#english) · [🇨🇳 中文](#chinese)

---

<a name="english"></a>

# transaction-receipt — On-chain Transaction Receipt Translator

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

AI Agent Skill for human-readable on-chain transaction receipts. Query tx status, fees, and token transfers across Ethereum, Bitcoin, and other chains. Automatic data source fallback with timeouts, rate limits, and response validation.

## ✨ Features

- 🔍 **Multi-chain Support**: EVM transactions (Ethereum, Base, Arbitrum, Optimism, etc.) and BTC transactions
- 🔄 **Smart Fallback**: Tokenview API + public RPC automatic switching
- ⚡ **Fast Response**: Timeout control, rate limiting, error handling
- 📊 **Human-Readable**: Plain language translation, no crypto jargon
- 🛡️ **Safe Output**: Never exposes API keys or raw JSON blobs

## 🚀 Quick Start

### Installation

```bash
openclaw skill install https://github.com/AntalphaAI/transaction-receipt
```

### Environment Variables (Optional)

| Variable | Required | Description |
|----------|----------|-------------|
| `TOKENVIEW_API_KEY` | No | Tokenview API Key. Falls back to public RPC if unset. Get one at [tokenview.io](https://tokenview.io) |
| `TRANSACTION_RECEIPT_MAX_PER_HOUR` | No | Hourly query limit per user, default 30 |
| `TRANSACTION_RECEIPT_RATE_FILE` | No | Custom path for rate limit state file |

### Usage

Simply send a transaction hash in chat:

- **EVM Transaction**: `0x1234567890abcdef...` (66 chars, starts with `0x`)
- **BTC Transaction**: `abcdef1234567890...` (64 chars, no `0x` prefix)

## 📋 Output Example

```
🚥 Status: ✅ Success

🧾 Transaction Overview
- Chain: Ethereum Mainnet
- Tx Hash: 0x12ab...89ef
- Block: 18234567
- Confirmations: 18

💸 Fund Flow
- From: 0xabcd...1234
- To: 0x5678...efgh
- Amount: 10.00 USDT

⛽ Gas Fee
- Used: 63,197
- Cost: 0.000010 ETH

Data aggregated by Antalpha AI
```

## 🔧 Technical Details

### Supported Chains

| Chain | Type | Data Source |
|-------|------|-------------|
| Ethereum | EVM | Tokenview / publicnode.com |
| Bitcoin | UTXO | Tokenview / blockstream.info |
| Base | EVM | Tokenview / public RPC |
| Arbitrum | EVM | Tokenview / public RPC |
| Optimism | EVM | Tokenview / public RPC |

### Rate Limiting

- Default: 30 queries per hour per user
- Configurable via `TRANSACTION_RECEIPT_MAX_PER_HOUR`
- State persisted at `~/.openclaw/state/transaction-receipt/rate-limit.log`

### Transaction Classification

The skill auto-classifies transactions:

| Type | Description |
|------|-------------|
| Simple Transfer | Native or ERC-20 token transfer |
| Swap / Trade | DEX aggregation, router calls |
| ⚠️ Approve | ERC-20 spending authorization (warning tone) |
| DeFi | Stake / deposit / withdraw / claim |
| NFT | ERC-721 / ERC-1155 mint or transfer |
| Contract Call | Generic smart contract interaction |

## 📁 Project Structure

```
transaction-receipt/
├── SKILL.md          # Skill definition (OpenClaw format)
├── README.md         # This file
├── LICENSE           # MIT License
└── .gitignore
```

## 📄 License

MIT License — see [LICENSE](LICENSE) for details.

## 🔗 Links

- **GitHub**: https://github.com/AntalphaAI/transaction-receipt
- **OpenClaw Docs**: https://docs.openclaw.ai
- **Antalpha AI**: https://github.com/AntalphaAI

---

*Built with ❤️ by Antalpha*

---

<a name="chinese"></a>

# transaction-receipt — 链上交易收据解析器

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

AI Agent 技能，将链上交易转化为人类可读的收据。支持以太坊、比特币及其他链的交易状态、手续费和代币转账查询，自动降级数据源，内置超时控制、限流和响应校验。

## ✨ 功能特性

- 🔍 **多链支持**：EVM 链（以太坊、Base、Arbitrum、Optimism 等）及 BTC 交易
- 🔄 **智能降级**：Tokenview API + 公共 RPC 自动切换
- ⚡ **响应迅速**：超时控制、限流保护、错误处理
- 📊 **人类可读**：白话文翻译，无需理解链上术语
- 🛡️ **安全输出**：不暴露 API Key 和原始 JSON 数据

## 🚀 快速开始

### 安装

```bash
openclaw skill install https://github.com/AntalphaAI/transaction-receipt
```

### 环境变量（可选）

| 变量 | 是否必须 | 说明 |
|------|----------|------|
| `TOKENVIEW_API_KEY` | 否 | Tokenview API Key，未设置时回退到公共 RPC。可在 [tokenview.io](https://tokenview.io) 免费获取 |
| `TRANSACTION_RECEIPT_MAX_PER_HOUR` | 否 | 每用户每小时查询上限，默认 30 次 |
| `TRANSACTION_RECEIPT_RATE_FILE` | 否 | 限流状态文件自定义路径 |

### 新手引导

首次使用建议配置 `TOKENVIEW_API_KEY`，获取更丰富的数据：

1. 前往 [tokenview.io](https://tokenview.io) 注册并获取 API Key
2. 在 OpenClaw 环境配置中添加：`TOKENVIEW_API_KEY=your_key_here`
3. 未配置 Key 时，技能自动使用公共 RPC 数据源（可能速度稍慢）

### 使用方式

在对话中直接发送交易哈希即可：

- **EVM 交易**：`0x1234567890abcdef...`（66 位，`0x` 开头）
- **BTC 交易**：`abcdef1234567890...`（64 位，无 `0x` 前缀）

## 📋 输出示例

```
🚥 状态: ✅ 成功

🧾 交易概览
- 链：以太坊主网
- 交易哈希：0x12ab...89ef
- 区块：18234567
- 确认数：18

💸 资金流向
- 发送方：0xabcd...1234
- 接收方：0x5678...efgh
- 金额：10.00 USDT

⛽ Gas 费用
- Gas 使用量：63,197
- 费用：0.000010 ETH

Data aggregated by Antalpha AI
```

## 🔧 技术细节

### 支持链

| 链 | 类型 | 数据来源 |
|----|------|----------|
| Ethereum | EVM | Tokenview / publicnode.com |
| Bitcoin | UTXO | Tokenview / blockstream.info |
| Base | EVM | Tokenview / 公共 RPC |
| Arbitrum | EVM | Tokenview / 公共 RPC |
| Optimism | EVM | Tokenview / 公共 RPC |

### 限流机制

- 默认每用户每小时 30 次查询
- 可通过 `TRANSACTION_RECEIPT_MAX_PER_HOUR` 调整
- 状态文件路径：`~/.openclaw/state/transaction-receipt/rate-limit.log`

### 交易类型识别

技能自动分类交易类型：

| 类型 | 说明 |
|------|------|
| 普通转账 | 原生代币或 ERC-20 转账 |
| 兑换 / 交易 | DEX 聚合器、路由合约调用 |
| ⚠️ 授权 | ERC-20 消费授权（高亮警示）|
| DeFi 操作 | 质押 / 存款 / 取款 / 领取奖励 |
| NFT | ERC-721 / ERC-1155 铸造或转移 |
| 合约调用 | 通用智能合约交互 |

## 📁 项目结构

```
transaction-receipt/
├── SKILL.md          # Skill 定义文件（OpenClaw 格式）
├── README.md         # 本文档
├── LICENSE           # MIT 许可证
└── .gitignore
```

## 📄 许可证

MIT License — 详见 [LICENSE](LICENSE)

## 🔗 链接

- **GitHub**: https://github.com/AntalphaAI/transaction-receipt
- **OpenClaw 文档**: https://docs.openclaw.ai
- **Antalpha AI**: https://github.com/AntalphaAI

---

*Built with ❤️ by Antalpha*
