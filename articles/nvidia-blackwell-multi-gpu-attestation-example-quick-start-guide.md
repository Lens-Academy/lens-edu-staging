---
title: "Blackwell Multi-GPU Attestation Example — Quick Start Guide"
author:
  - "Nvidia"
source_url: "https://docs.nvidia.com/attestation/quick-start-guide/latest/attestation-examples/blackwell_multi_gpu.html"
published: 2026-08-01
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

## Blackwell Multi-GPU Attestation Example ^blackwell-multi-gpu-attestation-example

This page provides a complete example of attestation for NVIDIA Blackwell multi-GPU configurations.

> **Note:** Blackwell multi-GPU attestation for MPT configurations will be supported once driver support for Blackwell MPT is available.

## Overview ^overview

Multi-GPU Blackwell attestation is **identical** to Hopper and Blackwell single GPU attestation. The attestation process uses the same SDK, APIs, and process as single-GPU configurations. The SDK automatically detects all GPUs. The only difference is the **attestation output** includes multiple GPU entries in the `submods` section—one for each GPU with identical claim structures. Each GPU is attested independently (no topology or switch attestation).

## Performing Remote / Local Attestation with SDK ^performing-remote-local-attestation

For detailed instructions on how to execute attestation commands, collect evidence, request RIMs, and perform attestation, please see the [Blackwell GPU Attestation Example](https://docs.nvidia.com/attestation/quick-start-guide/latest/attestation-examples/blackwell_single_gpu.html). The commands and code are identical for single and multi-GPU configurations—the SDK automatically detects all GPUs.

**For complete code examples, refer to:**

-   [Remote Attestation (NRAS)](https://docs.nvidia.com/attestation/quick-start-guide/latest/attestation-examples/hopper_single_gpu.html#performing-remote-attestation-with-sdk)
    
-   [Local Attestation](https://docs.nvidia.com/attestation/quick-start-guide/latest/attestation-examples/hopper_single_gpu.html#performing-local-attestation-with-sdk)
    

**Example NRAS Token (Remote Verifier) - Multi-GPU**

Show token (JWT)

```
[
    [
        "JWT", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJOVi1BdHRlc3RhdGlvbi1TREsiLCJpYXQiOjE3NjEyODU0ODgsImV4cCI6MTc2MTI4OTA4OCwibmJmIjoxNzYxMjg1MzY4LCJqdGkiOiI1YWQ2M2NlNC1iYTk3LTQ5NzYtOThmZi04ZDgyMDI3NGNhY2YifQ.KmNy9wu2H3eNpliBadX58zdAeAVYP7jQscg_azPc7n4"
    ], 
    {
        "REMOTE_GPU_CLAIMS": 
        [
            [
                "JWT", "eyJraWQiOiJudi1lYXQta2lkLXN0Zy0yMDI1MTAyMzA3NDcyMzk1MS1hZTk1ZWY5ZS0wMTUzLTQ3ZDUtOTEyNy00ZjkwMTU1MTI2Y2YiLCJhbGciOiJFUzM4NCJ9.eyJzdWIiOiJOVklESUEtUExBVEZPUk0tQVRURVNUQVRJT04iLCJ4LW52aWRpYS12ZXIiOiIzLjAiLCJuYmYiOjE3NjEyODU0ODcsImlzcyI6Imh0dHBzOi8vbnJhcy5hdHRlc3RhdGlvbi1zdGcubnZpZGlhLmNvbSIsIngtbnZpZGlhLW92ZXJhbGwtYXR0LXJlc3VsdCI6dHJ1ZSwic3VibW9kcyI6eyJHUFUtMCI6WyJESUdFU1QiLFsiU0hBLTI1NiIsImIwOWE2MzkwNTM0NDYzYjJhZjIyMTg1NDBlNmI2ZGE2MDRmMGUwMzEwNWY5NTI2ODlhOGU5NzdmYTM0MjBjYTUiXV19LCJlYXRfbm9uY2UiOiI5MzFkOGRkMGFkZDIwM2FjM2Q4YjRmYmRlNzVlMTE1Mjc4ZWVmY2RjZWFjNWI4NzY3MWE3NDhmMzIzNjRkZmNiIiwiZXhwIjoxNzYxMjg5MDg3LCJpYXQiOjE3NjEyODU0ODcsImp0aSI6ImRkZmIwMjQ0LWI4YTMtNDdjMS04NWJjLTUxMDQ1MTYyZTY0MCJ9.QpluUrkJkS9owNGB7KCYcchfChdhYrg_Wln4bx53iwAKFU_6zHDUf_iIie8v8aLWEWD0ERGWHJZ5YyUrsJ_ELzam9ZQpiOsLqDvpaUq9FnpUGFvU6o8XdHymhZYOwg3t"
            ], 
            {
                "GPU-0": "eyJraWQiOiJudi1lYXQta2lkLXN0Zy0yMDI1MTAyMzA3NDcyMzk1MS1hZTk1ZWY5ZS0wMTUzLTQ3ZDUtOTEyNy00ZjkwMTU1MTI2Y2YiLCJhbGciOiJFUzM4NCJ9.eyJ4LW52aWRpYS1ncHUtZHJpdmVyLXJpbS1zY2hlbWEtdmFsaWRhdGVkIjp0cnVlLCJpc3MiOiJodHRwczovL25yYXMuYXR0ZXN0YXRpb24tc3RnLm52aWRpYS5jb20iLCJlYXRfbm9uY2UiOiI5MzFkOGRkMGFkZDIwM2FjM2Q4YjRmYmRlNzVlMTE1Mjc4ZWVmY2RjZWFjNWI4NzY3MWE3NDhmMzIzNjRkZmNiIiwieC1udmlkaWEtZ3B1LXZiaW9zLXJpbS1zaWduYXR1cmUtdmVyaWZpZWQiOnRydWUsIngtbnZpZGlhLWdwdS12Ymlvcy1yaW0tZmV0Y2hlZCI6dHJ1ZSwiZXhwIjoxNzYxMjg5MDg3LCJ4LW52aWRpYS1ncHUtZHJpdmVyLXJpbS12ZXJzaW9uLW1hdGNoIjp0cnVlLCJpYXQiOjE3NjEyODU0ODcsInVlaWQiOiI1Mzc2MDUyNjQwMTkzNTk1ODc3NDExMjQyMjU1MzE0OTEyNzYxNTI2MjI3NTMyODMiLCJqdGkiOiI4NGNhMzYyZC0zMDkxLTQzYjktYmFlZS0zMmZmMDlkMjcyOTAiLCJ4LW52aWRpYS1ncHUtYXR0ZXN0YXRpb24tcmVwb3J0LW5vbmNlLW1hdGNoIjp0cnVlLCJ4LW52aWRpYS1ncHUtdmJpb3MtaW5kZXgtbm8tY29uZmxpY3QiOnRydWUsInNlY2Jvb3QiOnRydWUsIngtbnZpZGlhLWdwdS1kcml2ZXItcmltLWNlcnQtY2hhaW4iOnsieC1udmlkaWEtY2VydC1zdGF0dXMiOiJ2YWxpZCIsIngtbnZpZGlhLWNlcnQtb2NzcC1zdGF0dXMiOiJnb29kIiwieC1udmlkaWEtY2VydC1leHBpcmF0aW9uLWRhdGUiOiIyMDI3LTAyLTE2VDE5OjU3OjI0WiIsIngtbnZpZGlhLWNlcnQtcmV2b2NhdGlvbi1yZWFzb24iOm51bGx9LCJ4LW52aWRpYS1ncHUtdmJpb3MtcmltLWNlcnQtY2hhaW4iOnsieC1udmlkaWEtY2VydC1zdGF0dXMiOiJ2YWxpZCIsIngtbnZpZGlhLWNlcnQtb2NzcC1zdGF0dXMiOiJnb29kIiwieC1udmlkaWEtY2VydC1leHBpcmF0aW9uLWRhdGUiOiIyMDI2LTA3LTE1VDIzOjAyOjEwWiIsIngtbnZpZGlhLWNlcnQtcmV2b2NhdGlvbi1yZWFzb24iOm51bGx9LCJ4LW52aWRpYS1ncHUtYXR0ZXN0YXRpb24tcmVwb3J0LXBhcnNlZCI6dHJ1ZSwieC1udmlkaWEtZ3B1LWF0dGVzdGF0aW9uLXJlcG9ydC1jZXJ0LWNoYWluIjp7IngtbnZpZGlhLWNlcnQtc3RhdHVzIjoidmFsaWQiLCJ4LW52aWRpYS1jZXJ0LW9jc3Atc3RhdHVzIjoiZ29vZCIsIngtbnZpZGlhLWNlcnQtZXhwaXJhdGlvbi1kYXRlIjoiOTk5OS0xMi0zMVQyMzo1OTo1OVoiLCJ4LW52aWRpYS1jZXJ0LXJldm9jYXRpb24tcmVhc29uIjpudWxsfSwieC1udmlkaWEtZ3B1LWRyaXZlci1yaW0tc2lnbmF0dXJlLXZlcmlmaWVkIjp0cnVlLCJ4LW52aWRpYS1ncHUtYXJjaC1jaGVjayI6dHJ1ZSwieC1udmlkaWEtZ3B1LXZiaW9zLXJpbS12ZXJzaW9uLW1hdGNoIjp0cnVlLCJ4LW52aWRpYS1hdHRlc3RhdGlvbi13YXJuaW5nIjpudWxsLCJuYmYiOjE3NjEyODU0ODcsIngtbnZpZGlhLWdwdS1kcml2ZXItdmVyc2lvbiI6IjU3NS4yOCIsIngtbnZpZGlhLWdwdS1kcml2ZXItcmltLW1lYXN1cmVtZW50cy1hdmFpbGFibGUiOnRydWUsIngtbnZpZGlhLWdwdS1hdHRlc3RhdGlvbi1yZXBvcnQtc2lnbmF0dXJlLXZlcmlmaWVkIjp0cnVlLCJod21vZGVsIjoiR0gxMDAgQTAxIEdTUCBCUk9NIiwiZGJnc3RhdCI6ImRpc2FibGVkIiwieC1udmlkaWEtZ3B1LWRyaXZlci1yaW0tZmV0Y2hlZCI6dHJ1ZSwieC1udmlkaWEtZ3B1LWF0dGVzdGF0aW9uLXJlcG9ydC1jZXJ0LWNoYWluLWZ3aWQtbWF0Y2giOnRydWUsIm9lbWlkIjoiNTcwMyIsIngtbnZpZGlhLWdwdS12Ymlvcy1yaW0tc2NoZW1hLXZhbGlkYXRlZCI6dHJ1ZSwibWVhc3JlcyI6InN1Y2Nlc3MiLCJ4LW52aWRpYS1ncHUtdmJpb3MtdmVyc2lvbiI6Ijk2LjAwLkFGLjAwLjAxIiwieC1udmlkaWEtZ3B1LXZiaW9zLXJpbS1tZWFzdXJlbWVudHMtYXZhaWxhYmxlIjp0cnVlfQ.DL_i1GEBU5Znz_W8awCxs7TgaSfGYy_W-uGSo1pt0xUAtr-MEexUjoA0x0yjhWZE3fCUa4ekp2ZikdyVabC38MIc4mhrJwFUJJzD5E-VZPLJF1jeSegfbCHz6yK4BwP-",
                "GPU-1": "eyJra...",
                "GPU-2": "eyJra..."
            }
        ]
    }
]
```

**Example Local Verifier Token - Multi-GPU**

Show token (JWT)

```
[
    [
        "JWT", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJOVi1BdHRlc3RhdGlvbi1TREsiLCJpYXQiOjE3NjEyODYzNTksImV4cCI6MTc2MTI4OTk1OSwibmJmIjoxNzYxMjg2MjM5LCJqdGkiOiI3Yjc5MDViNS0xZWQzLTQwNDktOTE5OS1iYWM3ZWNmM2M4ZGIifQ.QFTvCLph963cAJmIInPSe7bqubvpd8l6y5hHc1lGaiM"
    ], 
    {
        "LOCAL_GPU_CLAIMS": 
        [
            [
                "JWT", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJOVklESUEtUExBVEZPUk0tQVRURVNUQVRJT04iLCJuYmYiOjE3NjEyODYyMzksImV4cCI6MTc2MTI4OTk1OSwiaWF0IjoxNzYxMjg2MzU5LCJqdGkiOiI3Y2JjNTY4Yy01ZGZlLTQ1ZWEtOTc0ZS0wMDhlM2U4Y2UzNmQiLCJ4LW52aWRpYS12ZXIiOiIzLjAiLCJpc3MiOiJMT0NBTF9HUFVfVkVSSUZJRVIiLCJ4LW52aWRpYS1vdmVyYWxsLWF0dC1yZXN1bHQiOnRydWUsInN1Ym1vZHMiOnsiR1BVLTAiOlsiRElHRVNUIixbIlNIQTI1NiIsIjdmNGI5NTM3NDAxMzY3M2RjOTg4MjRkNTY0ZGVkNThkMzhjZjE4MDI0MjM4NTA3ZWFmOGY3MWY5Yjc3YTA4ZDIiXV19LCJlYXRfbm9uY2UiOiI5MzFkOGRkMGFkZDIwM2FjM2Q4YjRmYmRlNzVlMTE1Mjc4ZWVmY2RjZWFjNWI4NzY3MWE3NDhmMzIzNjRkZmNiIn0.gNJyW6nt79UgyyTPqz2EG2ztAx9b-bB73msNa2SMpOU"
            ], 
            {
                "GPU-0": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJtZWFzcmVzIjoic3VjY2VzcyIsIngtbnZpZGlhLWdwdS1hcmNoLWNoZWNrIjp0cnVlLCJ4LW52aWRpYS1ncHUtZHJpdmVyLXZlcnNpb24iOiI1NzUuMjgiLCJ4LW52aWRpYS1ncHUtdmJpb3MtdmVyc2lvbiI6Ijk2LjAwLkFGLjAwLjAxIiwieC1udmlkaWEtZ3B1LWF0dGVzdGF0aW9uLXJlcG9ydC1jZXJ0LWNoYWluIjp7IngtbnZpZGlhLWNlcnQtZXhwaXJhdGlvbi1kYXRlIjoiOTk5OS0xMi0zMVQyMzo1OTo1OSIsIngtbnZpZGlhLWNlcnQtc3RhdHVzIjoidmFsaWQiLCJ4LW52aWRpYS1jZXJ0LW9jc3Atc3RhdHVzIjoiZ29vZCIsIngtbnZpZGlhLWNlcnQtcmV2b2NhdGlvbi1yZWFzb24iOm51bGx9LCJ4LW52aWRpYS1ncHUtYXR0ZXN0YXRpb24tcmVwb3J0LWNlcnQtY2hhaW4tZndpZC1tYXRjaCI6dHJ1ZSwieC1udmlkaWEtZ3B1LWF0dGVzdGF0aW9uLXJlcG9ydC1wYXJzZWQiOnRydWUsIngtbnZpZGlhLWdwdS1hdHRlc3RhdGlvbi1yZXBvcnQtbm9uY2UtbWF0Y2giOnRydWUsIngtbnZpZGlhLWdwdS1hdHRlc3RhdGlvbi1yZXBvcnQtc2lnbmF0dXJlLXZlcmlmaWVkIjp0cnVlLCJ4LW52aWRpYS1ncHUtZHJpdmVyLXJpbS1mZXRjaGVkIjp0cnVlLCJ4LW52aWRpYS1ncHUtZHJpdmVyLXJpbS1zY2hlbWEtdmFsaWRhdGVkIjp0cnVlLCJ4LW52aWRpYS1ncHUtZHJpdmVyLXJpbS1jZXJ0LWNoYWluIjp7IngtbnZpZGlhLWNlcnQtZXhwaXJhdGlvbi1kYXRlIjoiMjAyNy0wMi0xNlQxOTo1NzoyNCIsIngtbnZpZGlhLWNlcnQtc3RhdHVzIjoidmFsaWQiLCJ4LW52aWRpYS1jZXJ0LW9jc3Atc3RhdHVzIjoiZ29vZCIsIngtbnZpZGlhLWNlcnQtcmV2b2NhdGlvbi1yZWFzb24iOm51bGx9LCJ4LW52aWRpYS1ncHUtZHJpdmVyLXJpbS1zaWduYXR1cmUtdmVyaWZpZWQiOnRydWUsIngtbnZpZGlhLWdwdS1kcml2ZXItcmltLXZlcnNpb24tbWF0Y2giOnRydWUsIngtbnZpZGlhLWdwdS1kcml2ZXItcmltLW1lYXN1cmVtZW50cy1hdmFpbGFibGUiOnRydWUsIngtbnZpZGlhLWdwdS12Ymlvcy1yaW0tZmV0Y2hlZCI6dHJ1ZSwieC1udmlkaWEtZ3B1LXZiaW9zLXJpbS1zY2hlbWEtdmFsaWRhdGVkIjp0cnVlLCJ4LW52aWRpYS1ncHUtdmJpb3MtcmltLWNlcnQtY2hhaW4iOnsieC1udmlkaWEtY2VydC1leHBpcmF0aW9uLWRhdGUiOiIyMDI2LTA3LTE1VDIzOjAyOjEwIiwieC1udmlkaWEtY2VydC1zdGF0dXMiOiJ2YWxpZCIsIngtbnZpZGlhLWNlcnQtb2NzcC1zdGF0dXMiOiJnb29kIiwieC1udmlkaWEtY2VydC1yZXZvY2F0aW9uLXJlYXNvbiI6bnVsbH0sIngtbnZpZGlhLWdwdS12Ymlvcy1yaW0tdmVyc2lvbi1tYXRjaCI6dHJ1ZSwieC1udmlkaWEtZ3B1LXZiaW9zLXJpbS1zaWduYXR1cmUtdmVyaWZpZWQiOnRydWUsIngtbnZpZGlhLWdwdS12Ymlvcy1yaW0tbWVhc3VyZW1lbnRzLWF2YWlsYWJsZSI6dHJ1ZSwieC1udmlkaWEtZ3B1LXZiaW9zLWluZGV4LW5vLWNvbmZsaWN0Ijp0cnVlLCJzZWNib290Ijp0cnVlLCJkYmdzdGF0IjoiZGlzYWJsZWQiLCJlYXRfbm9uY2UiOiI5MzFkOGRkMGFkZDIwM2FjM2Q4YjRmYmRlNzVlMTE1Mjc4ZWVmY2RjZWFjNWI4NzY3MWE3NDhmMzIzNjRkZmNiIiwiaHdtb2RlbCI6IkdIMTAwIEEwMSBHU1AgQlJPTSIsInVlaWQiOiI1Mzc2MDUyNjQwMTkzNTk1ODc3NDExMjQyMjU1MzE0OTEyNzYxNTI2MjI3NTMyODMiLCJvZW1pZCI6IjU3MDMiLCJpc3MiOiJMT0NBTF9HUFVfVkVSSUZJRVIiLCJuYmYiOjE3NjEyODYyMzksImV4cCI6MTc2MTI4OTk1OSwiaWF0IjoxNzYxMjg2MzU5LCJqdGkiOiJiMmZkMjc0Ni02YmZlLTRjMDQtYTlhOC03OGIxZmVmMzMxNWIifQ.w1XkCq5RpF46yHGAwrjLagM4GKENvu3UjkXITYTn3LQ",
                "GPU-1": "eyJra...",
                "GPU-2": "eyJra..."
            }
        ]
    }
]
```

## Claims ^claims

In multi-GPU configurations, each GPU (GPU-0, GPU-1, GPU-2, etc.) is attested independently, producing identical claim structures for each device. The only difference from single GPU attestation is that the token contains multiple GPU entries—one for each GPU in the system.

The claims structure for Blackwell GPUs is identical to Hopper GPUs. For detailed information about the individual GPU claims returned in the attestation token, refer to:

-   [Remote GPU Claims](https://docs.nvidia.com/attestation/quick-start-guide/latest/attestation-examples/hopper_single_gpu.html#decoded-nras-token)
    
-   [Local GPU Claims](https://docs.nvidia.com/attestation/quick-start-guide/latest/attestation-examples/hopper_single_gpu.html#decoded-local-verifier-token)
    

## Validating Multi-GPU Attestation Results ^validating-multi-gpu-attestation-results

You can validate the attestation token against a policy file. For sample policy files, refer to the [policies directory](https://github.com/NVIDIA/nvtrust/tree/main/guest_tools/attestation_sdk/tests/policies) in the nvtrust repository.

```python
import json

# Load policy from file
with open("policy.json", "r") as f:
    policy = json.load(f)

# Validate token against policy
result = client.validate_token(json.dumps(policy))
print("[Validation] Result: " + str(result))
```

## Additional Resources ^additional-resources

-   Review additional attestation examples for more scenarios and advanced usage. See the **[Attestation Examples](https://docs.nvidia.com/attestation/quick-start-guide/latest/attestation-examples/index.html)** for a complete list.
    
-   Learn how to transition from proof-of-concept to production deployment, including NGC onboarding and integration options: **[POC to Production Guide](https://docs.nvidia.com/attestation/poc-to-production/latest/deployment_guide.html)**.
    
-   Learn about our **[Attestation Client Tools](https://docs.nvidia.com/attestation/attestation-client-tools-sdk/latest/sdk_introduction.html)**, **[Cloud Services](https://docs.nvidia.com/attestation/cloud-services/latest/nras/nras_introduction.html)** and **[Advanced documentation](https://docs.nvidia.com/attestation/advanced-documentation/latest/claims-guide/index.html)**.
