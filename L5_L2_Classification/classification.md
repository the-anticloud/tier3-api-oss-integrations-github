# L5 Narrow / L2 General Classification — api-oss-integrations-github
**Platform:** Anticloud | **PAX:** 27B | **IP:** USPTO pending 2026, Anticloud FZ LLE
**Domain:** Sovereign GitHub integration: PR analysis, issue triage, code review via PAX 27B

## L5 Narrow
api-oss-integrations-github specializes in sovereign github integration: pr analysis, issue triage, code review via pax 27b within the Anticloud sovereign deployment boundary. All operations stay local — no cloud services, no external APIs, no data exfiltration. The narrow scope ensures deterministic, auditable behavior that PAX 27B can reason about precisely.

## L2 General
L2 General means api-oss-integrations-github is available to all 9 Anticloud tiers without per-tier configuration. The same API serves hospital, defense, robotics, and research deployments.

## PAX Integration
PAX 27B reviews pull requests: checks for AIOSS integration, compliance with tier conventions, security vulnerabilities, and code quality. All analysis is local — GitHub repo content is cloned locally before PAX processes it.

## AIOSS Audit Relevance
Every GitHub event (repo + PR/issue hash + PAX analysis hash + action taken) is AIOSS-chained: H_n = SHA3-256(H_{n-1} || entry_hash_n || timestamp_n).
Tamper-evident, offline-verifiable, zero cloud dependency.

## Regulatory / Compliance
NIST SSDF (secure code review), ISO 27001 A.14.2 (development security)
