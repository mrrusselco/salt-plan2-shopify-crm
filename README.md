# 🍰 Salt Lagos — Integrated Order & CRM System (Plan 2)
### Shopify + HubSpot CRM (or Zoho CRM)

> A full-stack order management and customer relationship system for Salt Lagos — unifying Shopify, Gmail, WhatsApp, and social media into one CRM, with marketing automation, customer profiles, and department workflows built in.

---

## 📋 Overview

Plan 2 upgrades Salt Lagos from a basic order tracker to a complete **customer intelligence and operations platform**. Shopify acts as the commerce engine, feeding directly into a CRM (HubSpot or Zoho) which becomes the single hub for all five order channels, customer history, marketing automation, and management reporting.

**What Plan 2 adds over Plan 1:**
- Full customer profiles (order history, lifetime value, preferences, acquisition source)
- Repeat order tracking and win-back automation
- Birthday campaigns, seasonal promotions, post-event follow-ups
- Omnichannel CRM inbox (email + WhatsApp + Instagram/Facebook DMs in one place)
- Revenue forecasting and marketing performance dashboards
- Social media enquiry → conversion tracking

---

## 📁 Repository Structure

```
salt-order-system-plan2/
├── dashboard/
│   └── sweetorder-dashboard.jsx       # React dashboard component (CRM-connected)
├── docs/
│   └── salt-plan2-shopify-crm.html    # Full system overview document
├── crm/
│   ├── hubspot-setup.md               # HubSpot CRM configuration guide
│   ├── zoho-setup.md                  # Zoho CRM configuration guide (alternative)
│   └── pipeline-stages.md             # CRM deal pipeline stage definitions
├── automations/
│   ├── order-workflows.md             # Order confirmation, dispatch, completion flows
│   └── marketing-workflows.md         # Birthday, win-back, seasonal campaign flows
└── README.md
```

---

## ⚙️ Tech Stack

| Layer | Tool |
|---|---|
| CRM (Recommended) | [HubSpot CRM](https://hubspot.com) — Free → Starter ($15–50/mo) |
| CRM (Alternative) | [Zoho CRM](https://zoho.com/crm) — Free (3 users) → Standard ($14/user/mo) |
| E-commerce | Shopify (existing store, native CRM integration) |
| Email | Gmail (info@saltlagos.com, events@saltlagos.com) |
| Messaging | WhatsApp Business API via Twilio |
| Social | Meta Business Suite (Instagram + Facebook) |
| Dashboard | React (JSX) |
| Automation bridge | Zapier (optional — only for edge cases) |

---

## 🔌 Order Channels

| Channel | Integration Method | CRM Action | Auto-Response |
|---|---|---|---|
| 🛒 Shopify | Native CRM plugin (1-click) | Creates/updates customer record + deal | Shopify native confirmation + CRM follow-up sequence |
| ✉️ Gmail | CRM Gmail plugin | Email logged to customer profile; unread flagged | CRM-triggered acknowledgement email |
| 💬 WhatsApp | WhatsApp Business + Twilio | Message logged as CRM ticket | Auto-reply redirect to website |
| 📱 Instagram/Facebook | CRM Social Inbox (HubSpot/Zoho Social) | DM logged; enquiry ticket created | Auto-DM: redirect to saltlagos.com |
| ☎️ Phone | Manual CRM entry by staff | Call outcome logged to customer record | Staff sends WhatsApp/email post-call |

---

## 🧠 CRM Options — HubSpot vs Zoho

### HubSpot CRM ⭐ Recommended Starting Point

Best for Salt Lagos to begin with — genuinely powerful free tier, clean UI, and native Shopify integration that syncs historical and live orders automatically.

**Strengths:**
- Free forever (core CRM, unlimited contacts, unlimited users)
- One-click Shopify integration — syncs orders, customers, products in real time
- Native Facebook and Instagram inbox
- Gmail plugin logs emails automatically to customer records
- Built-in email marketing with visual automation builder
- E-commerce dashboards auto-generated from Shopify data

**Limitations:**
- Marketing automation requires paid Marketing Hub ($50+/mo) for advanced flows
- Can become feature-heavy for a small team

**Cost:** Free → Starter $15/user/mo → Marketing Hub from $50/mo

---

### Zoho CRM — Best Value on Paid Tier

Better omnichannel support out of the box. WhatsApp, social, email, and phone all managed natively without extra connectors. More affordable than HubSpot when scaling beyond the free tier.

**Strengths:**
- Full omnichannel inbox (WhatsApp + social + email + phone) in standard plan
- Social media DM management and tracking built in
- Workflow automation included — no extra cost
- Zoho Desk for support tickets (converts social DMs to tickets)
- Multicurrency support (₦ Naira + USD + GBP for international orders)
- More affordable at scale

**Limitations:**
- Steeper initial configuration than HubSpot
- UI less polished; takes longer to learn

**Cost:** Free (3 users) → Standard $14/user/mo → Professional $23/user/mo

---

## 🚨 Unread Email Alert System (CRM-Native)

1. Customer sends order email to `info@saltlagos.com` or `events@saltlagos.com`
2. CRM Gmail plugin detects the email and logs it to the customer's profile
3. CRM marks it as an **unread ticket** in the unified inbox
4. CRM triggers a **task alert** assigned to Sales/Admin: *"Follow up on order email from [Customer] within 2 hours"*
5. A WhatsApp alert fires to the Sales team via Twilio integration
6. An **auto-acknowledgement email** is sent to the customer immediately
7. The ticket remains unresolved in the CRM inbox until Sales/Admin responds and marks it resolved

---

## 📊 Order Pipeline (CRM Deal Stages)

```
New Enquiry → Confirmed → In Production → Ready / Out for Delivery → Completed
```

Each stage change in the CRM triggers automated actions:

| Stage | Automated Action |
|---|---|
| **New Enquiry** | WhatsApp alert to Sales, auto-reply to customer, unread badge in CRM |
| **Confirmed** | CRM task created for Kitchen team with order details and required completion date |
| **In Production** | Kitchen status updated; management dashboard reflects live production count |
| **Out for Delivery** | Customer receives WhatsApp/email: *"Your Salt Lagos order is on its way! 🍰 Refrigerate immediately upon arrival."* |
| **Completed** | Customer lifetime value updated; review request sent 24h later; marketing segments updated |

---

## 🤖 Automation Workflows

### Order Automations

```
New Shopify Order
  → CRM creates deal
  → Sales/Admin notified in CRM inbox
  → Internal WhatsApp alert fires
  → Customer confirmation email sent

Unread Email Detected
  → CRM flags as unread ticket
  → Task assigned to Sales (due: 2 hours)
  → Auto-acknowledgement sent to customer

Order Confirmed by Sales
  → CRM triggers Kitchen task notification
  → Status updates to "In Production"
  → Kitchen team WhatsApp group messaged

Order Dispatched
  → Customer WhatsApp + email: delivery update + care instructions
  → Status updates to "Out for Delivery"

Order Completed
  → Customer lifetime value recalculated
  → Review request email sent (24h delay)
  → Customer enrolled in appropriate marketing segment
```

### Marketing Automations

```
Birthday Campaign
  → Trigger: Contact birthday field = 7 days from today
  → Action: Send personalised email with link to saltlagos.com

Win-Back Sequence
  → Trigger: Last order date > 60 days ago
  → Action 1 (Day 1): "We miss you at Salt Lagos 🍰" email
  → Action 2 (Day 7): Follow-up with new menu highlights

Post-Event Follow-Up
  → Trigger: Order tagged as "Event" and status = Completed
  → Action (14 days later): Email requesting feedback and referrals

Seasonal Campaigns
  → Trigger: Manual segment (e.g. ordered in Dec 2025)
  → Action: Targeted email for Christmas / Valentine's / Easter orders

Social Lead Nurture
  → Trigger: Social DM enquiry logged but no order placed in 7 days
  → Action 1 (Day 3): Email showcasing Salt's menu and testimonials
  → Action 2 (Day 7): Follow-up with a call to action to order
```

---

## 🏗️ Setup Instructions

### Prerequisites
- HubSpot account (free) **or** Zoho CRM account
- Shopify store admin access
- Gmail admin access (info@ and events@)
- WhatsApp Business account + Twilio account
- Meta Business Suite admin access (Instagram + Facebook)
- Node.js 18+ (for the React dashboard)

---

### 1. Connect Shopify to the CRM

**HubSpot:**
1. In HubSpot → App Marketplace → search "Shopify"
2. Install the native Shopify integration
3. Authorise with your Shopify store URL (`saltlagos.myshopify.com`)
4. All historical orders and customers sync automatically within minutes
5. New orders sync in real time going forward

**Zoho CRM:**
1. In Zoho CRM → Settings → Marketplace → search "Shopify"
2. Install the Shopify for Zoho CRM extension
3. Map Shopify order fields to Zoho deal fields
4. Configure sync direction (Shopify → Zoho for orders)

---

### 2. Connect Gmail

**HubSpot:**
Install the [HubSpot Sales Chrome Extension](https://chrome.google.com/webstore/detail/hubspot-sales/oiiaigjnkhngdbnoookogelabohpglmd). Log in and connect the Gmail accounts (`info@` and `events@`). Emails sent and received will auto-log to matching contact records.

**Zoho CRM:**
In Zoho → Settings → Email → Add Gmail accounts. Enable "Email Intelligence" to auto-associate emails with contacts and deals.

---

### 3. Connect WhatsApp via Twilio

```bash
# Install Twilio CLI (optional, for advanced configuration)
npm install -g twilio-cli
```

1. Create a [Twilio account](https://twilio.com) and activate a WhatsApp sender
2. In HubSpot: Settings → Inbox → Connect WhatsApp → enter Twilio credentials
3. In Zoho: Settings → Channels → WhatsApp → connect Twilio
4. Set up the auto-redirect message template in Twilio:
   ```
   Hi! Thanks for reaching out to Salt Lagos 🍰
   To place your order, please visit: saltlagos.com
   Or email us: info@saltlagos.com
   ```

---

### 4. Connect Social Media (Instagram + Facebook)

**HubSpot:**
Settings → Inbox → Connect a channel → Facebook Messenger / Instagram DMs → authorise Meta Business Suite. All incoming DMs appear in the HubSpot inbox alongside email and WhatsApp.

**Zoho CRM:**
Zoho Social → Settings → connect Instagram Business and Facebook Page. DMs and comments flow into Zoho's social inbox and can be converted to CRM leads/tickets.

**Meta Business Suite Auto-Reply (set regardless of CRM):**
Meta Business Suite → Inbox → Automations → Instant Reply:
```
Hi! 🍰 Salt Lagos doesn't accept orders via DM.
To place your order, please visit: saltlagos.com
Or email us at: info@saltlagos.com
We look forward to serving you!
```

---

### 5. Dashboard — Local Development

```bash
# Clone the repo
git clone https://github.com/your-org/salt-order-system-plan2.git
cd salt-order-system-plan2

# Install dependencies
npm install

# Configure environment variables
cp .env.example .env
# Edit .env with your CRM API credentials
```

**.env configuration:**
```env
# HubSpot
VITE_HUBSPOT_API_KEY=your_hubspot_private_app_token

# OR Zoho CRM
VITE_ZOHO_CLIENT_ID=your_zoho_client_id
VITE_ZOHO_CLIENT_SECRET=your_zoho_client_secret
VITE_ZOHO_REFRESH_TOKEN=your_zoho_refresh_token
```

```bash
# Start development server
npm run dev
```

> ⚠️ Never commit your `.env` file. It is already listed in `.gitignore`.

---

## 💰 Monthly Cost Estimate

### Option A — HubSpot Free Start

| Tool | Cost |
|---|---|
| HubSpot CRM | Free |
| Shopify integration | Free |
| Gmail plugin | Free |
| WhatsApp via Twilio | ~$5–15/mo |
| Meta Business Suite | Free |
| **Total** | **~$5–15/mo (~₦7,000–20,000)** |

### Option B — HubSpot / Zoho Paid (Full Features)

| Tool | Cost |
|---|---|
| HubSpot Starter or Zoho Standard | $14–50/mo |
| WhatsApp via Twilio | ~$5–15/mo |
| Zapier (if needed for edge cases) | $0–20/mo |
| **Total** | **~$20–65/mo (~₦28,000–90,000)** |

---

## 🗺️ Implementation Timeline

| Phase | Tasks | Duration |
|---|---|---|
| 1 — CRM Setup | Create CRM, connect Shopify, install Gmail plugin, configure pipeline stages | Days 1–4 |
| 2 — Channel Integration | WhatsApp via Twilio, Meta social inbox, auto-reply DMs, unread alert workflow | Days 5–10 |
| 3 — Automations | Order workflows (confirm → kitchen, dispatch → customer), marketing automations | Days 11–16 |
| 4 — Dashboard & Training | Configure CRM dashboards per department, connect React dashboard, train staff | Days 17–24 |
| 5 — Marketing Activation | Launch first email campaign, activate birthday + win-back sequences | Week 5–6 |

---

## 📌 Business Context

- **Company:** Salt Lagos
- **Location:** 1B Namtl Waterplace, off 2nd Street, Osborne Foreshore Estate 1, Ikoyi, Lagos
- **Hours:** Monday–Saturday, 10am–5pm
- **Lead Time:** 48 hours minimum (96 hours for wedding cakes)
- **Delivery:** Limited zones within Lagos (Island + select Mainland areas)
- **Website:** [saltlagos.com](https://saltlagos.com)
- **Contact:** info@saltlagos.com · events@saltlagos.com · events@saltlagos.com

---

## 🔗 Related

- [Plan 1 — Zapier + Airtable](../salt-order-system-plan1/) — a lighter-weight implementation recommended as the immediate first step. Plan 2 is the recommended migration path after 6–12 months on Plan 1.

---

## 📄 License

Internal use only. © Salt Lagos 2026. All rights reserved.
