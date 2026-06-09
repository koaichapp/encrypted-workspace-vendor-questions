# 20 questions every workspace-tool vendor should answer

A free security questionnaire for evaluating any workspace, messaging, or storage vendor. CC-BY-4.0 — reuse with attribution. Canonical: <https://koaich.com/vendor-questions>.

The recurring theme: **a vendor that holds your keys can read your content; a vendor that doesn't, can't.** Most of these questions exist to find out which one you're dealing with.

## Key custody & recovery

**1. Who holds the encryption keys to my data?**
If the vendor holds them, they can decrypt your content whenever they choose, are compelled to, or are compromised. The only strong answer is one where the keys never reach the vendor's servers.

**2. Where are encryption keys generated?**
Keys generated on your device and never transmitted to the server are the strongest property. Keys generated server-side by the vendor are weaker by an order of magnitude.

**3. If I lose my password, can you recover my data?**
If "yes," the vendor holds a copy of your data somewhere they can decrypt. The honest answer for a zero-knowledge vendor is "no — recovery is through your own devices/recovery material."

## Data access (the vendor's side)

**4. What can your support engineers see when I open a ticket?**
Most vendors' support tooling can read customer content directly. "We can't read it" should be backed by architecture, not policy.

**5. What can your engineers see with full database admin access?**
"Encrypted at rest" is satisfied by a database file that's encrypted even when the vendor holds the keys. "The admin sees ciphertext" requires end-to-end encryption with user-held keys.

**6. Can you produce a list of every employee role with access to my workspace?**
Vendors that haven't audited this internally probably can't answer. Vendors that give an honest answer — even an uncomfortable one — are doing the work.

## AI & training

**7. When your AI features operate on my content, where does the content go?**
Common patterns: (1) sent to the vendor's own model, retained for training; (2) sent to a third-party model provider; (3) processed with no retention. Each has very different privacy properties.

**8. Is my content used to train AI models, by you or by your sub-processors?**
Acceptable answers vary ("no," "yes by default, opt-out available," "never"). What matters is that it's specific and verifiable.

**9. Can your AI features run without the vendor's servers being able to read my content in the clear?**
Be skeptical — most workspace AI needs cleartext access on the server to operate. Ask exactly where the boundary is.

## Legal & transparency

**10. If you receive a legal request for my data, what can you produce?**
A vendor that holds the keys can produce content. A vendor that doesn't can only produce metadata. A privacy policy doesn't change what the architecture allows.

**11. Do you publish a transparency report listing the data requests you receive?**
Vendors that publish this (Signal, Apple, Cloudflare, Microsoft) show their work. Vendors that don't are choosing not to be auditable on this dimension.

**12. Have you ever produced customer content in response to a third-party request?**
A direct question with a direct answer. Evasiveness is itself informative.

## Breach posture

**13. Have you been breached? When? What was exposed?**
Every vendor of scale is breached eventually. What matters is what an attacker walked away with — cleartext, or ciphertext they can't open.

**14. If your production infrastructure were compromised tomorrow, what could the attacker decrypt?**
The most revealing question. A vendor holding cleartext or vendor-held keys answers "everything." A vendor with end-to-end encryption answers "ciphertext only."

**15. Do you have a published incident-response policy?**
The policy's contents matter less than the fact that one exists. Mature vendors have one.

## Verifiability

**16. Is your security model documented publicly, with cryptographic specifics?**
Vague "bank-grade security" marketing is a red flag. Named primitives, key hierarchies, and threat models are a green one.

**17. Has your encryption been independently audited?**
"Not yet, audit scheduled" is acceptable for a new vendor. "We don't need one" is not.

**18. Can I verify that the code you ship matches the code you publish?**
For native apps: reproducible builds + signature verification. For web: a code-transparency log or similar. Most vendors can't; the ones that can take security seriously.

## Supply chain & continuity

**19. Can you list your sub-processors, where each operates, and what data each touches?**
Every vendor uses sub-processors. The question is whether each receives cleartext or ciphertext — handing cleartext to a CDN multiplies the attack surface.

**20. What happens to my data if you're acquired?**
Acquisition is the most common way a privacy posture changes without users noticing. Vendors with cryptographic guarantees can answer honestly; vendors with policy guarantees often can't.

---

*Maintained by [Koaich](https://koaich.com). CC-BY-4.0 — attribution to koaich.com/vendor-questions. Corrections: open an issue or email hello@koaich.com.*
