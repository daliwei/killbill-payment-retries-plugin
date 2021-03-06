killbill-payment-retries-plugin
===============================

Kill Bill Payment Control plugin to control payment retries.

Release builds are available on [Maven Central](http://search.maven.org/#search%7Cga%7C1%7Cg%3A%22org.kill-bill.billing.plugin.java%22%20AND%20a%3A%22payment-retries-plugin%22) with coordinates `org.kill-bill.billing.plugin.java:payment-retries-plugin`.

Kill Bill compatibility
-----------------------

| Plugin version | Kill Bill version |
| -------------: | ----------------: |
| 0.0.y          | 0.16.z            |
| 0.2.y          | 0.18.z            |


Usage
-----

### Private endpoints

Verify the status of a payment method associated with a failed payment:

```
curl -v \
     -u admin:password \
     -H "X-Killbill-ApiKey: bob" \
     -H "X-Killbill-ApiSecret: lazar" \
     "http://127.0.0.1:8080/plugins/payment-retries-plugin/paymentMethodCheck?paymentExternalKey=XXX"
```

List current configuration:

```
curl -v \
     -u admin:password \
     -H "X-Killbill-ApiKey: bob" \
     -H "X-Killbill-ApiSecret: lazar" \
     "http://127.0.0.1:8080/plugins/payment-retries-plugin/configuration"
```

Filter for retryable errors only:

```
curl -v \
     -u admin:password \
     -H "X-Killbill-ApiKey: bob" \
     -H "X-Killbill-ApiSecret: lazar" \
     "http://127.0.0.1:8080/plugins/payment-retries-plugin/configuration?retryable=true"
```

Filter for insufficient funds errors only (see [ErrorMessage](https://github.com/killbill/killbill-payment-retries-plugin/blob/master/src/main/java/org/killbill/billing/plugin/payment/retries/rules/ErrorMessage.java)):

```
curl -v \
     -u admin:password \
     -H "X-Killbill-ApiKey: bob" \
     -H "X-Killbill-ApiSecret: lazar" \
     "http://127.0.0.1:8080/plugins/payment-retries-plugin/configuration?errorMessage=INSUFFICIENT_FUNDS"
```
