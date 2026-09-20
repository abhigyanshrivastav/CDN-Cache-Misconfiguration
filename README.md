# CDN Cache Misconfiguration / Web Cache Deception on Aakash i-Tutor

## Overview

This repository documents a security assessment of a **CDN cache misconfiguration** identified in the quiz and examination section of the Aakash i-Tutor platform.

The investigation focused on how cached responses associated with authenticated exam resources could remain accessible through client-side cache data, despite cache-control directives being present in the HTTP responses.

## Investigation

The issue was investigated by analyzing HTTP requests, responses, cache behavior, and response headers using:

- **Burp Suite**
- **Website Sniffer**

During testing, cached resources associated with the quiz environment were observed in the browser's cache. Further analysis showed that exam-related content, including question data and answer information, could be recovered from cached files without directly opening or completing the corresponding test.

The original security report identified the behavior as a **cache configuration issue rather than a conventional application bug**, with characteristics similar to **Web Cache Deception**.

## Reproduction Summary

The documented reproduction process involved:

1. Loading the quiz/examination environment.
2. Allowing the relevant resources to load.
3. Examining the browser's cached data.
4. Identifying cached resources associated with the examination.
5. Inspecting the contents of the cached files.
6. Recovering encoded response data containing examination-related information.
7. Demonstrating that answer information could be accessed from cached data even when the corresponding test had not been opened.

The original report includes screenshots documenting the cache entries, extracted response data, questions, and answer information.

## Observed Impact

The investigation documented potential exposure of:

- Examination questions
- Answer information
- Cached response metadata
- Confidential examination-related resources

The report further noted potential misuse of exposed examination information, including possible impact on competitive examination outcomes.

## Technical Classification

**Issue:** CDN Cache Misconfiguration  
**Related Concept:** Web Cache Deception  
**Affected Area:** Quiz / Examination resources  
**Testing Tools:** Burp Suite, Website Sniffer

## Documentation

The complete technical investigation, reproduction steps, screenshots, and evidence are available in the accompanying security report:

**[CDN Cache Misconfiguration — Security Report](./CDM_CM%20%282%29.pdf)**

> **Note:** The report documents the behavior observed during the original investigation. It does not provide a confirmed permanent remediation; the original report explicitly stated that a permanent solution had not yet been established.

## Responsible Disclosure

This repository is intended for **security research, documentation, and educational purposes**. The material reflects observations documented during the original assessment and should not be used to access, modify, or disclose information belonging to systems or users without authorization.

## Tools Used

- [Burp Suite](https://portswigger.net/burp)
- Website Sniffer
