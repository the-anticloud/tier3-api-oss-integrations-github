# Developer Cookbook — api-oss-integrations-github
**Stack:** Python 3.11, PyGithub, PAX 27B, AIOSS_FORMAT
**Domain:** Sovereign GitHub integration: PR analysis, issue triage, code review via PAX 27B
**License:** Apache-2.0 | **IP:** USPTO pending 2026, Anticloud FZ LLE

## Core Usage

```python
from api_oss_integrations_github import GitHubIntegration
gh = GitHubIntegration(token=vault.retrieve('gh_token'), aioss_chain='./github.aioss')
review = gh.review_pr(repo='kleinnner/Anticloud', pr=42, pax_model='./pax-27b-q4.gguf')
print(review.summary, review.security_flags)
```

## AIOSS Chain Append

```python
import hashlib, time

def aioss_append(chain_path, payload: bytes, module_id: str):
    entry_hash = hashlib.sha3_256(payload).digest()
    ts = int(time.time_ns()).to_bytes(8, 'big')
    with open(chain_path, 'rb') as f:
        f.seek(-32, 2); prev_hash = f.read(32)
    new_hash = hashlib.sha3_256(prev_hash + entry_hash + ts).digest()
    with open(chain_path, 'ab') as f:
        f.write(ts + entry_hash + new_hash)
    return new_hash.hex()

# After every api-oss-integrations-github output:
chain_hash = aioss_append("./api_oss_integrations_github.aioss",
                           result_bytes, "api-oss-integrations-github")
```

## Performance & Integration

Performance: profile with api-oss-devtools. Benchmark with api-oss-analytics. Integration: all api-oss-integrations-github operations are logged to api-oss-logging and audited by api-oss-compliance.
