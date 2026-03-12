# email-rpc
What if we could re-implement the entire modern world of email as a single coherently designed system?

Also it seems like it would be cool to have the robots email each other? Or to be able to send each other messages on the cli? Or if you could just apt-get install and entire e2e email tool?

# Protocols and Interfaces

```
mail.proto                  ← user-facing model (what you send/receive)
mime.proto                  ← wire format codec (message ↔ bytes)
smtp.proto                  ← transport (envelope + delivery)
submission.proto            ← MSA: client → mail system boundary
imap.proto                  ← stateful retrieval
pop.proto                   ← simple retrieval
jmap.proto                  ← modern retrieval/sync
sieve.proto                 ← server-side filtering
delivery.proto              ← orchestration (ties everything together)

dns/
  mx.proto                  ← mail server discovery
  spf.proto                 ← IP authorization
  dkim.proto                ← cryptographic signatures
  dmarc.proto               ← policy + alignment
  arc.proto                 ← forwarding chain authentication
  tls_policy.proto          ← transport security (MTA-STS + DANE)
  autoconfig.proto          ← client service discovery
  bimi.proto                ← brand indicators

list.proto                  ← mailing list headers + unsubscribe
mdn.proto                   ← read receipts / disposition notifications
crypto.proto                ← end-to-end encryption (S/MIME + PGP)
calendar.proto              ← meeting invitations (iMIP/iTIP)
reputation.proto            ← feedback loops + deliverability
bounce.proto                ← bounce classification + processing
```
