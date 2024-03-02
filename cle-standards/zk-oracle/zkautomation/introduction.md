# Introduction

Developers can use ZK Automation by deploying their automation program through ORA’s Web App. They simply need to specify their target contract, target function, and source (when to trigger). For more complex trigger conditions, developers can choose to either trigger automation every N-th block (in scenarios like a keeper bot) or use a CLE as the offchain source.

CLEs for ZK Automation can be built from scratch, migrated from CLEs for ZK Indexing or existing subgraphs, or by reusing deployed ones. If developers choose to migrate from an existing CLE for ZK Indexing, they only need to change the Meta App type of that CLE to make it a valid source for ZK Automation.

Once the ZK Automation job has been registered (and the CLE has been optionally deployed), the corresponding ZK Automation service will start and automation jobs will be executed when the trigger condition is met.
