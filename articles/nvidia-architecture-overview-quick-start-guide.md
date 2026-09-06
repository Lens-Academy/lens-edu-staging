---
title: "Architecture Overview — Quick Start Guide"
author:
  - "Nvidia"
source_url: "https://docs.nvidia.com/attestation/quick-start-guide/latest/architecture.html"
published: 2026-09-06
created: 2026-09-06
accessed: 2026-09-06
llm-review:
  date: 2026-09-06
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-06
    kind: "live"
description:
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

## Attestation Suite Architecture Overview ^attestation-suite-architecture-overview

The NVIDIA Attestation Suite is composed of several interconnected services and components that work together to provide a comprehensive verification solution. Understanding this architecture is key to leveraging the full power of the suite.

### Overall Architecture Diagram ^overall-architecture-diagram

The following diagram illustrates the flow of information and trust between the client, the NVIDIA services, and the GPU hardware.

![Architecture Diagram](https://docs.nvidia.com/attestation/quick-start-guide/latest/_images/arch.jpg)

## How It Works: A Simplified View ^how-it-works-a

The attestation process provides a complete, verifiable chain of trust.

1.  **Generate Evidence**: Use the Attestation SDK to collect cryptographic evidence from the GPU and other NVIDIA devices.
    
2.  **Fetch Golden Measurements**: The RIM Service provides the official, signed “golden” measurements for authentic NVIDIA components.
    
3.  **Attest and Verify**: The NVIDIA Remote Attestation Service or the Local verifier compares the evidence against the golden measurements to provide a definitive verification result.
    

## Core Components ^core-components

### Client-Side Components ^client-side-components

-   **Attestation SDK**: A Python-based SDK that provides high-level APIs for developers to integrate attestation into their applications. It orchestrates interactions with the GPU driver and remote services.
    
-   **Attestation CLI**: A command-line interface, bundled with the SDK, for performing ad-hoc local gpu attestation. It is built on top of the Python Attestation SDK.
    
-   **Local GPU Verifier**: The underlying logic that extracts evidence from the GPU. It interacts with the NVIDIA driver via NVML to retrieve measurements and certificates.
    

### Cloud Services ^cloud-services

-   **RIM Service**: The Reference Integrity Manifest (RIM) Service is responsible for hosting the “golden” measurements. It stores and serves signed RIMs, which contain the authoritative measurement values for authentic NVIDIA hardware and software.
    
-   **NVIDIA Remote Attestation Service (NRAS)**: A cloud service that performs remote attestation. It receives attestation evidence from the client, fetches the appropriate RIM, appraises the evidence, and returns a signed attestation result.
    
-   **Certificate Revocation Service**: An OCSP-based service used to check the revocation status of NVIDIA device identity certificates and RIM signing certificates, ensuring that revoked or compromised certificates are not trusted.
    

## Next Steps ^next-steps

Now that you have successfully attested your GPU and understand the architecture, explore the detailed documentation for each component:

-   Learn how to transition from proof-of-concept to production deployment, including NGC onboarding and integration options: **[POC to Production Guide](https://docs.nvidia.com/attestation/poc-to-production/latest/deployment_guide.html)**.
    
-   Learn about our **[Attestation Client Tools](https://docs.nvidia.com/attestation/attestation-client-tools-sdk/latest/sdk_introduction.html)**, **[Cloud Services](https://docs.nvidia.com/attestation/cloud-services/latest/nras/nras_introduction.html)** and **[Advanced documentation](https://docs.nvidia.com/attestation/advanced-documentation/latest/claims-guide/index.html)**.
