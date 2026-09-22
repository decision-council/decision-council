<p align="center">
  <a href="https://veristria.com">
    <img src="https://veristria.com/brand/veristria-mark-circle-512.png" alt="Veristria" width="100" height="100">
  </a>
</p>

<h1 align="center">Veristria</h1>

<h3 align="center">Proof over promises.</h3>

<p align="center">
  <strong>Verification for AI-built software.</strong><br>
  Find exposed secrets. Check data access. Catch payment leaks.
</p>

<p align="center">
  <a href="https://veristria.com">Website</a> &nbsp;·&nbsp;
  <a href="https://veristria.com/products">Products</a> &nbsp;·&nbsp;
  <a href="https://veristria.com/blog">Writing</a> &nbsp;·&nbsp;
  <a href="https://veristria.com/security">Security</a> &nbsp;·&nbsp;
  <a href="mailto:support@teamveristria.com">Contact</a>
</p>

---

## The build passed. What did it expose?

A working application can still ship a server secret to the browser, expose a database table, or leave a payment unreconciled.

**Veristria is an independent Norwegian security company focused on what happens after code ships.** We build targeted checks for the gap between what an application was supposed to do and what its deployed systems actually do.

Not another confidence score. A finding you can inspect and act on.

## Three products. Three critical questions.

| Product | The question | What it checks |
| :--- | :--- | :--- |
| **[KeyDrift](https://keydrift.dev)** | Did a secret reach the browser? | Scans served JavaScript for exposed credentials, distinguishing server-side secrets from intentionally public keys. |
| **[RowShield](https://rowshield.dev)** | What can an anonymous visitor read? | Checks public access to Supabase data. Connected audits examine row-level security policies and track drift. |
| **[FeeGuard](https://feeguard.dev)** | What did a refund leave behind? | Audits Stripe Connect records for application fees left after refunds, unreversed transfers, and other reconciliation gaps. |

**Each product offers a free first check.** Start with a deployed URL for KeyDrift or RowShield, or pasted Stripe Connect export data for FeeGuard. Deeper audits and ongoing monitoring depend on the product and its connection requirements.

## A finding should come with evidence

```text
Inspect what is deployed
          ↓
Capture checkable evidence
          ↓
Explain what needs to change
```

**Evidence you can inspect.** A served file, a query result, or a payment record—not a warning with nothing behind it. Our published demo receipts include evidence files and SHA-256 hashes for checking file integrity.

**Access kept narrow.** Public surfaces where possible; scoped credentials where needed. Detection should not require permission to change the system it examines.

**A concrete next step.** Findings should help you identify the exposed credential, correct the policy, or understand the missing payment action.

[See the published evidence on our website →](https://veristria.com)

## Behind Veristria

I'm **Lars O. Horpestad**, Veristria's founder and a Norwegian AI author. I wrote *Å ta smartere beslutninger med AI* (2023), a practical guide to large language models.

My focus at Veristria is the other side of AI-assisted development: helping teams verify the software they now have the tools to build. KeyDrift, RowShield, and FeeGuard turn that focus into specific, checkable answers.

[More about Veristria](https://veristria.com/about) · [Founder background](https://veristria.com/press)

## Read, explore, get in touch

We write about deployed-code verification, practical AI security, Supabase access controls, and Stripe Connect reconciliation on the **[Veristria blog](https://veristria.com/blog)**.

For product questions and collaboration, contact **[support@teamveristria.com](mailto:support@teamveristria.com)**.

For vulnerabilities, use **[security@teamveristria.com](mailto:security@teamveristria.com)** and follow our [disclosure guidance](https://veristria.com/security). Please keep credentials and sensitive findings out of public issues.

---

<p align="center">
  <strong>Build with AI. Verify what ships.</strong><br>
  <sub>Founder-led · Norway · Veristria</sub>
</p>
