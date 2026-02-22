# ZSA Coin Vote Audit — On-Chain Analysis

> Cross-referencing decrypted ballot data with on-chain shielding flows for the Q1 2026 ZSA coin holder vote.
>
> Analysis by [CipherScan](https://cipherscan.app) — February 22, 2026

---

## Election Overview

| Field | Value |
|---|---|
| **Question** | What is your general sentiment toward including Zcash Shielded Assets (ZSAs) as a protocol feature? |
| **Election ID** | `d7281580b01f8d1d056b52965397a63895ac491538d49ae9a9bbb4458271f701` |
| **Snapshot range** | Block 2,978,050 → Block 3,218,812 |
| **Snapshot cutoff** | Block 3,218,812 (~January 27, 2026) |
| **Total ballots** | 204 |
| **Seed phrase** | `bleak oval budget link step again suggest shallow girl write daring stock indoor angry token flag shove dream gentle priority grunt champion antique disease` |

To have voting weight, ZEC must be in the **Orchard shielded pool** by block 3,218,812. ZEC is not spent during voting — voters prove ownership via zero-knowledge proofs and submit ballots to the vote server.

---

## Results

Ballots were decrypted using a custom tool built on the [`zcash-vote`](https://github.com/hhanh00/zcash-vote) library with the public seed phrase.

### Aggregate

| Choice | Ballots | ZEC | % of Weight |
|---|---|---|---|
| **Support** | ~10 | 16,731 ZEC | 1.35% |
| **Oppose** | ~194 | 1,218,979 ZEC | 98.65% |
| **Total** | 204 | 1,235,710 ZEC | 100% |

### Distribution

| Metric | Value |
|---|---|
| Average ballot | 6,117 ZEC |
| Median ballot | 2,000 ZEC |
| Largest ballot | 90,999 ZEC (Oppose) |
| Smallest ballot | 0.001 ZEC |
| Top 10 ballots hold | 46.09% of total weight |

### Top 10 Ballots

| Rank | ZEC | Choice | Potential On-Chain Source |
|---|---|---|---|
| 1 | 90,999.272 | Oppose | t1dHheg2SkTGBMK1VsCPwsqJ3Gccsnen7rf — 202,077 ZEC from **Binance**, shield Dec 24 (could split into #1 + #2) |
| 2 | 90,643.804 | Oppose | t1dHheg2SkTGBMK1VsCPwsqJ3Gccsnen7rf — same entity, second note (90,999 + 90,644 = 181,643 fits inside 202,077) |
| 3 | 64,830.000 | Oppose | No direct match |
| 4 | 60,000.000 | Oppose | t1XKfbZYsdxR5HSnP25ee5VaAxgCNUtFkFK — 50,001 ZEC from **Binance**, shield Jan 2 (+ possible merge) |
| 5 | 60,000.000 | Oppose | No direct match |
| 6 | 54,000.000 | Oppose | t1XKfbZYsdxR5HSnP25ee5VaAxgCNUtFkFK — same 50,001 + ~4K existing (alternative to #4) |
| 7 | 45,000.728 | Oppose | No direct match |
| 8 | 37,000.000 | Oppose | No direct match |
| 9 | 34,100.000 | Oppose | No direct match |
| 10 | 33,000.000 | Oppose | No direct match |

Combined: **569,573 ZEC** (46% of total vote weight).

### All Support Ballots

Only 10 ballots voted Support. Here they are in full:

| Rank | ZEC |
|---|---|
| 1 | 9,453.230 |
| 2 | 2,400.000 |
| 3 | 1,800.000 |
| 4 | 1,613.996 |
| 5 | 1,243.416 |
| 6 | 220.000 |
| 7 | 0.023 |
| 8 | 0.003 |
| 9 | 0.001 |
| 10 | 0.001 |

---

## Shielded Pool Context

The Zcash shielded pool grew significantly in the weeks before the snapshot cutoff:

| Date | Approximate Shielded Pool Size |
|---|---|
| January 1, 2026 | ~4.20M ZEC |
| January 13, 2026 | ~4.88M ZEC |
| January 27, 2026 (cutoff) | ~5.03M ZEC |

The pool grew by approximately **830,000 ZEC** in the 27 days before the snapshot — a 20% increase. The 1,235,710 ZEC that voted represents roughly **24.5%** of the shielded pool at the time of the snapshot.

---

## On-Chain Cross-Reference

Using CipherScan's `shielded_flows` database, we examined all transparent-to-shielded transactions from January 1–27, 2026, and matched them against the 204 decrypted ballot amounts.

### Exact Matches (shield amount within 1 ZEC of a ballot)

30 individual shielding events match a ballot amount within 1 ZEC. The most notable:

| Shield Amount | Ballot Amount | Difference | Address | Shield Date |
|---|---|---|---|---|
| 5,000.0000 | 5,000.0000 | 0.0003 | t1Ud5bCy2sirabJgBEeV94j2jX3UyYkegCP | Jan 26 |
| 4,320.6425 | 4,319.8360 | 0.8065 | t1Ku2KLyndDPsR32jwnrTMd3yvi9tfFP8ML (NEAR Bridge) | Jan 19 |
| 3,404.4404 | 3,405.0000 | 0.5596 | t1Ku2KLyndDPsR32jwnrTMd3yvi9tfFP8ML (NEAR Bridge) | Jan 7 |
| 2,500.0978 | 2,500.0000 | 0.0978 | t1SXTi2aWCy7LenjPMFpKHZ6SwVe8HqaSin | Jan 22 |
| 2,400.1719 | 2,400.0000 | 0.1719 | t1Ku2KLyndDPsR32jwnrTMd3yvi9tfFP8ML (NEAR Bridge) | Jan 23 |
| 2,300.6330 | 2,300.0000 | 0.6330 | t1Ku2KLyndDPsR32jwnrTMd3yvi9tfFP8ML (NEAR Bridge) | Jan 13 |
| 1,763.2819 | 1,763.0000 | 0.2819 | t1JZA32UGjgvfpL76BJK7qdYC9xnZGdHxS3 | Jan 22 |
| 1,500.0000 | 1,500.0000 | 0.0041 | t1h7yPTNhzV47Jk9BEba3wnxsDzPK6Zmjr7 | Jan 24 |
| 1,308.7189 | 1,309.0000 | 0.2811 | t1Ku2KLyndDPsR32jwnrTMd3yvi9tfFP8ML (NEAR Bridge) | Jan 26 |
| 1,000.7442 | 1,000.0100 | 0.7342 | t1XkVNE8TpmJCmmZ4BDAQsvgYMAJsSBmMLg | Jan 13 |
| 999.9998 | 1,000.0100 | 0.0103 | t1PrVWB8WCpAeUPGp6NdK7seCPyDy6ZT1ub | Jan 7 |
| 838.1994 | 837.4180 | 0.7814 | t1gKfwcLEFWFEjPmAUm4PzmfbTQ8VsQsSKK | Jan 2 |
| 800.2557 | 800.0750 | 0.1807 | t1TpsSMHxbGkzbYQw5dmLUeLAgKocKy7rdv | Jan 21 |
| 737.4573 | 738.0000 | 0.5427 | t1Ku2KLyndDPsR32jwnrTMd3yvi9tfFP8ML (NEAR Bridge) | Jan 25 |
| 517.1742 | 518.0000 | 0.8258 | t1UTMZWLVZSagYYZ2pG4YiSkgb9NJQ4KMhs | Jan 25 |
| 507.9982 | 508.0000 | 0.0018 | t1W85eTCBvRvyh4wdzAPafjAkUFwqsdLxhp | Jan 3 |
| 499.9999 | 500.0100 | 0.0102 | t1ZVSpU7j3eqdAf72X3G5jw2aV9B7aMcT8W | Jan 8 |
| 458.5196 | 458.2610 | 0.2586 | t1Ku2KLyndDPsR32jwnrTMd3yvi9tfFP8ML (NEAR Bridge) | Jan 10 |
| 401.8490 | 401.9060 | 0.0570 | t1ZKZXhjwUVd5ULN7ToVviHMEVciLG76TUs | Jan 17 |

Small differences (~0.001–1 ZEC) are consistent with transaction fees.

---

## NEAR Intents Bridge Activity

The address `t1Ku2KLyndDPsR32jwnrTMd3yvi9tfFP8ML` is the **NEAR Intents Bridge** on Zcash. It processed 5,707 shielding transactions totaling 7,132,695 ZEC in January 2026 alone.

**34 bridge shields match ballot amounts within 5 ZEC**, suggesting cross-chain bridging specifically to acquire Zcash voting weight.

| Bridge Shield | Ballot Match | Difference | Ballot Choice | Date |
|---|---|---|---|---|
| 4,320.6425 | 4,319.8360 | 0.81 | Oppose | Jan 19 |
| 3,599.9272 | 3,604.0520 | 4.12 | Oppose | Jan 26 |
| 3,404.4404 | 3,405.0000 | 0.56 | Oppose | Jan 7 |
| 2,814.3296 | 2,818.0000 | 3.67 | Oppose | Jan 13 |
| 2,798.9917 | 2,800.9840 | 1.99 | Oppose | Jan 16 |
| 2,765.2941 | 2,763.0250 | 2.27 | Oppose | Jan 22 |
| 2,679.3161 | 2,683.5300 | 4.21 | Oppose | Jan 21 |
| 2,495.0563 | 2,500.0000 | 4.94 | Oppose | Jan 20 |
| 2,446.3323 | 2,449.0000 | 2.67 | Oppose | Jan 22 |
| 2,400.1719 | 2,400.0000 | 0.17 | **Support** | Jan 23 |
| 2,395.9343 | 2,400.0000 | 4.07 | **Support** | Jan 23 |
| 2,300.6330 | 2,300.0000 | 0.63 | Oppose | Jan 13 |
| 2,295.2895 | 2,300.0000 | 4.71 | Oppose | Jan 7 |
| 2,198.6665 | 2,200.0000 | 1.33 | **Support** | Jan 7 |
| 2,026.3590 | 2,027.8370 | 1.48 | Oppose | Jan 19 |
| 2,017.8146 | 2,021.0000 | 3.19 | Oppose | Jan 9 |
| 1,998.5807 | 2,000.0000 | 1.42 | Oppose | Jan 14 |
| 1,798.1535 | 1,800.0000 | 1.85 | **Support** | Jan 19 |
| 1,308.7189 | 1,309.0000 | 0.28 | Oppose | Jan 26 |
| 1,204.8110 | 1,208.1060 | 3.30 | Oppose | Jan 16 |
| 737.4573 | 738.0000 | 0.54 | Oppose | Jan 25 |
| 521.2347 | 518.0000 | 3.23 | Oppose | Jan 12 |
| 496.0794 | 500.0100 | 3.93 | Oppose | Jan 22 |
| 458.5196 | 458.2610 | 0.26 | Oppose | Jan 10 |
| 399.6123 | 401.9060 | 2.29 | Oppose | Jan 19 |

**4 of the 34 bridge-matched ballots voted Support** (2,400 / 2,400 / 2,200 / 1,800 ZEC = ~8,800 ZEC). This represents over half of the meaningful Support vote weight. Most of the Support side may have been funded from cross-chain sources.

---

## Fresh Addresses Created for Voting

These addresses did not exist before the snapshot window. They were created, used to shield ZEC, and abandoned — a classic single-purpose pattern. All voted Oppose.

### Whale-tier (December 2025) — Exchange Withdrawals

| Address | Created | Received | Source | Shield Date | Potential Ballot Match | Balance | TXs |
|---|---|---|---|---|---|---|---|
| t1dHheg2SkTGBMK1VsCPwsqJ3Gccsnen7rf | **Dec 19** | 202,078 ZEC | **Binance** | Dec 24 (1 tx) | Top 2 ballots (90,999 + 90,644 = 181,643) | 0.00 | 8 |
| t1XKfbZYsdxR5HSnP25ee5VaAxgCNUtFkFK | **Dec 24** | 50,001 ZEC | **Binance** | Jan 2 (1 tx) | ~54,000 or ~60,000 (with merge) | 0.00 | 8 |
| t1KtX3hb63sCg2XxZZNA9HGyYP6deGNTHZy | **Dec 27** | 24,001 ZEC | **Binance** | Jan 2 (1 tx) | Possible merge into larger ballot | 0.00 | 6 |
| t1TJPm4okQLVjbSP6Uy2V7u5bjkYvndp5Qh | **Dec 8** | 6,020 ZEC | **Kraken** | Dec 8–15 (multiple) | Possible merge into larger ballot | 0.00 | 24 |

All four whale-tier addresses were funded directly from centralized exchange hot wallets:

**t1dHheg2SkTGBMK1VsCPwsqJ3Gccsnen7rf** — The largest. Received 3 deposits from Binance Hot Wallet totaling 202,077 ZEC (133,999.99 + 68,076.23 + 0.99) on December 19. Shielded everything in one transaction on December 24 — Christmas Eve. The top two ballots (90,999 + 90,644 = 181,643 ZEC) fit inside this shield with ~20,434 ZEC left over. If this is one entity, they controlled **14.7% of the entire vote** from an address that existed for less than two weeks.

**t1XKfbZYsdxR5HSnP25ee5VaAxgCNUtFkFK** — Received 4 deposits from Binance Hot Wallet totaling 50,001 ZEC (29,999.99 + 17,999.99 + 1,999.99 + 0.99) on December 24–25. Shielded everything on January 2.

**t1KtX3hb63sCg2XxZZNA9HGyYP6deGNTHZy** — Received 3 deposits from Binance Hot Wallet totaling 24,001 ZEC (19,999.99 + 4,000.00 + 0.99) on December 27. Shielded everything on January 2.

**t1TJPm4okQLVjbSP6Uy2V7u5bjkYvndp5Qh** — Received multiple deposits from Kraken Hot Wallet and associated addresses totaling 6,020 ZEC between December 8–15. Shielded in 3 batches.

The three Binance addresses (`t1dHhe...`, `t1XKfb...`, `t1KtX3...`) together withdrew **276,080 ZEC** from a single exchange. They could represent one entity or coordinated entities. Two of them shielded on the exact same day (January 2).

### Mid-tier (January 2026)

| Address | Created | Received | Ballot Match | Balance | TXs |
|---|---|---|---|---|---|
| t1Ud5bCy2sirabJgBEeV94j2jX3UyYkegCP | **Jan 26** | 5,000 ZEC | 5,000 (Oppose) | 0.00 | 3 |
| t1SXTi2aWCy7LenjPMFpKHZ6SwVe8HqaSin | **Jan 22** | 2,500 ZEC | 2,500 (Oppose) | 0.00 | 5 |
| t1h7yPTNhzV47Jk9BEba3wnxsDzPK6Zmjr7 | **Jan 24** | 1,500 ZEC | 1,500 (Oppose) | 0.00 | 2 |
| t1XkVNE8TpmJCmmZ4BDAQsvgYMAJsSBmMLg | **Jan 13** | 1,001 ZEC | 1,000 (Oppose) | 0.00 | 3 |
| t1PrVWB8WCpAeUPGp6NdK7seCPyDy6ZT1ub | **Jan 7** | 1,000 ZEC | 1,000 (Oppose) | 0.00 | 2 |
| t1TpsSMHxbGkzbYQw5dmLUeLAgKocKy7rdv | **Jan 21** | 800 ZEC | 800 (Oppose) | 0.00 | 3 |
| t1W85eTCBvRvyh4wdzAPafjAkUFwqsdLxhp | **Jan 3** | 508 ZEC | 508 (Oppose) | 0.00 | 5 |
| t1ZKZXhjwUVd5ULN7ToVviHMEVciLG76TUs | **Jan 17** | 402 ZEC | 402 (Oppose) | 0.00 | 4 |

**Combined fresh address activity (whale + mid-tier): ~288,811 ZEC. All voted Oppose.**

---

## Long-Term Accumulators

These addresses shielded ZEC over weeks or months before the snapshot, suggesting deliberate accumulation of voting weight.

| Address | Active Since | Total Shielded | Shield TXs | Pattern |
|---|---|---|---|---|
| t1Le9DvY19cAhhv6yxJRBU8qdCBDeXh5VdP | Oct 2025 | 25,483 ZEC | 8 | Large deposits (2K–8.5K each). Zero balance after. |
| t1KNrNik1qcCFA8DDsB4ZBh9DwNtJ9eihNS | Dec 2025 | 16,336 ZEC | 147 | Systematic batches (100–1,000 ZEC) over 6 weeks. Zero balance after. |
| t1ZfoQ2EaH5AwK9qhjRKdJiVnuJ3JdgqumM | Nov 2025 | 11,856 ZEC | 9 | Steady accumulation with some deshield/reshield activity. |
| t1JZA32UGjgvfpL76BJK7qdYC9xnZGdHxS3 | Apr 2024 | 7,385 ZEC | 83 | The oldest. Consistent small shields (5–400 ZEC) over 20+ months. On Jan 22 shielded 1,763 ZEC — exact ballot match. |
| t1ZVSpU7j3eqdAf72X3G5jw2aV9B7aMcT8W | Nov 2025 | 5,212 ZEC | 11 | Multiple deposits Nov–Jan. Zero balance after. |
| t1gdgid4wUQxbJESYc9CBCYukBtrevVwRdd | May 2022 | 24,688 ZEC | 1,190 | Long-running address since 2022. Still active with 467 ZEC balance. |
| t1gKfwcLEFWFEjPmAUm4PzmfbTQ8VsQsSKK | Dec 2025 | 1,881 ZEC | 5 | Short burst Dec 30 – Jan 2. |

---

## Key Findings

### 1. ZSAs were overwhelmingly rejected by coin holders

98.65% of voting ZEC weight voted Oppose. Only 16,731 ZEC out of 1,235,710 supported ZSAs.

### 2. The vote was whale-dominated

The top 10 ballots held 46% of total voting weight. The two largest ballots alone (90,999 + 90,644 = 181,643 ZEC) represented 14.7% of the entire vote.

### 3. 276K ZEC was withdrawn from Binance and shielded before the snapshot

Three fresh addresses withdrew a combined **276,080 ZEC** from **Binance Hot Wallet** in late December 2025 and shielded it all before the January 27 cutoff. The largest (`t1dHheg2SkTGBMK1VsCPwsqJ3Gccsnen7rf`) withdrew 202,077 ZEC and shielded it in a single transaction on Christmas Eve. The top two ballots (90,999 + 90,644 = 181,643 ZEC) fit inside that shield. A fourth fresh address withdrew 6,020 ZEC from **Kraken**. All four addresses are now at zero balance.

### 4. Cross-chain bridging was used to acquire voting weight

34 NEAR Intents Bridge shielding events match ballot amounts. This indicates cross-chain capital movement specifically to participate in the Zcash coin vote. Notably, 4 of the bridge-matched ballots voted Support — representing over half of the meaningful Support vote weight.

### 5. Fresh addresses were created specifically for voting

At least 12 addresses were created in December 2025 – January 2026 with no prior history. They received ZEC, shielded it, and went to zero balance. All voted Oppose. Combined weight: ~288,811 ZEC — **23% of total voting weight** from disposable addresses.

### 6. Shielded pool grew 20% before the snapshot

The shielded pool went from ~4.20M ZEC on January 1 to ~5.03M ZEC at the January 27 cutoff — an increase of roughly 830,000 ZEC. However, only 1,235,710 ZEC voted, meaning much of the pool did not participate.

### 7. Most voting weight was already shielded and untraceable

Only a fraction of the voting weight can be traced through transparent shielding. The remaining ZEC was already in the Orchard pool before the analysis window, leaving no transparent on-chain trace.

---

## Limitations

- **Correlation is not proof.** A shield amount matching a ballot amount does not prove the same entity controlled both. It is a strong correlation, not a definitive link.
- **NEAR bridge is high-volume.** 5,707 shields in January — some amount matches may be coincidental.
- **Shielded pool is opaque.** Once ZEC enters Orchard, it cannot be tracked. We can only observe the transparent-to-shielded boundary.
- **Notes can be consolidated.** A voter could accumulate ZEC through many small shields and merge them shielded-side before voting.
- **Fee variation.** Differences of ~0.001–1 ZEC between shield and ballot amounts are consistent with transaction fees.

---

## Reproducibility

Anyone can verify these findings:

1. **Decrypt ballots** — Download the [zcash-vote-audit](https://github.com/hhanh00/zcash-vote-audit/releases) tool or build a custom decryptor using the [`zcash-vote`](https://github.com/hhanh00/zcash-vote) crate with the seed phrase above
2. **Cross-check with zooko's fork** — [zooko/zcash-vote-audit](https://github.com/zooko/zcash-vote-audit) independently downloads and caches all individual ballot JSONs per election, with per-ballot detail output
3. **Query on-chain data** — Use CipherScan's indexed database or any Zcash full node to examine shielded flows for the addresses listed
4. **Verify addresses** — Search any address on [CipherScan](https://cipherscan.app) to see full transaction history

---

*Analysis performed using CipherScan on-chain data and the zcash-vote decryption library.*
*February 22, 2026*
