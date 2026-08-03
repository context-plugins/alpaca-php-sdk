
# Activity Type

- FILL
  Order fills (both partial and full fills)

- TRANS
  Cash transactions (both CSD and CSW)

- MISC
  Miscellaneous or rarely used activity types (All types except those in TRANS, DIV, or FILL)

- ACATC
  ACATS IN/OUT (Cash)

- ACATS
  ACATS IN/OUT (Securities)

- CFEE
  Crypto fee

- CSD
  Cash deposit(+)

- CSW
  Cash withdrawal(-)

- DIV
  Dividends

- DIVCGL
  Dividend (capital gain long term)

- DIVCGS
  Dividend (capital gain short term)

- DIVFEE
  Dividend fee

- DIVFT
  Dividend adjusted (Foreign Tax Withheld)

- DIVNRA
  Dividend adjusted (NRA Withheld)

- DIVROC
  Dividend return of capital

- DIVTW
  Dividend adjusted (Tefra Withheld)

- DIVTXEX
  Dividend (tax exempt)

- FEE
  Fee denominated in USD

- INT
  Interest (credit/margin)

- INTNRA
  Interest adjusted (NRA Withheld)

- INTTW
  Interest adjusted (Tefra Withheld)

- JNL
  Journal entry

- JNLC
  Journal entry (cash)

- JNLS
  Journal entry (stock)

- MA
  Merger/Acquisition

- NC
  Name change

- OPASN
  Option assignment

- OPEXP
  Option expiration

- OPXRC
  Option exercise

- PTC
  Pass Thru Charge

- PTR
  Pass Thru Rebate

- REORG
  Reorg CA

- SC
  Symbol change

- SSO
  Stock spinoff

- SSP
  Stock split

## Enumeration

`ActivityType`

## Fields

| Name |
|  --- |
| `FILL` |
| `TRANS` |
| `MISC` |
| `ACATC` |
| `ACATS` |
| `CSD` |
| `CSW` |
| `DIV` |
| `DIVCGL` |
| `DIVCGS` |
| `DIVFEE` |
| `DIVFT` |
| `DIVNRA` |
| `DIVROC` |
| `DIVTW` |
| `DIVTXEX` |
| `INT` |
| `INTNRA` |
| `INTTW` |
| `JNL` |
| `JNLC` |
| `JNLS` |
| `MA` |
| `NC` |
| `OPASN` |
| `OPEXP` |
| `OPXRC` |
| `PTC` |
| `PTR` |
| `REORG` |
| `SC` |
| `SSO` |
| `SSP` |
| `CFEE` |
| `FEE` |

## Example

```php
use TraderApiLib\Models\ActivityType;

$activityType = ActivityType::DIVTW;
```

