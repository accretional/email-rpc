# email-rpc
What if we could re-implement the entire modern world of email as a single coherently designed system?

Also it seems like it would be cool to have the robots email each other? Or to be able to send each other messages on the cli? Or if you could just apt-get install and entire e2e email tool?

# Protocols and Interfaces

```
mail.proto                  ← user-facing model (what you send/receive)
mime.proto                  ← wire format codec (message ↔ bytes)
smtp.proto                  ← transport (envelope + relay delivery)
submission.proto            ← MSA: client → mail system trust boundary
lmtp.proto                  ← final hop: MTA → message store
queue.proto                 ← MTA queue lifecycle & retry policy
imap.proto                  ← stateful retrieval
pop.proto                   ← simple retrieval
jmap.proto                  ← modern retrieval/sync
sieve.proto                 ← server-side filtering
milter.proto                ← MTA filter plugin protocol
scanning.proto              ← content analysis (spam/phish/malware)
trace.proto                 ← message path & received headers
delivery.proto              ← orchestration (full inbound + outbound pipeline)

dns/
  mx.proto                  ← mail server discovery
  spf.proto                 ← IP authorization
  dkim.proto                ← cryptographic signatures
  dmarc.proto               ← policy + alignment
  arc.proto                 ← forwarding chain authentication
  tls_policy.proto          ← transport security (MTA-STS + DANE)
  autoconfig.proto          ← client service discovery
  bimi.proto                ← brand indicators
  dnsbl.proto               ← DNS blocklists

srs.proto                   ← sender rewriting (forwarding + SPF compat)
eai.proto                   ← internationalized addresses (UTF-8, IDNA)
list.proto                  ← mailing list headers + unsubscribe
mdn.proto                   ← read receipts / disposition notifications
crypto.proto                ← end-to-end encryption (S/MIME + PGP)
calendar.proto              ← meeting invitations (iMIP/iTIP)
reputation.proto            ← feedback loops + deliverability
bounce.proto                ← bounce classification + processing
```
