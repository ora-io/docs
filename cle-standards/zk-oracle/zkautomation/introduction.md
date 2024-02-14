# Introduction

Developers can use zkAutomation by deploying their automation program through Ora's Web App. They simply need to specify their target contract, target function, and source (when to trigger). For more complex trigger conditions, developers can choose to either trigger automation every N-th block (in scenarios like a keeper bot) or use a CLE as the off-chain source.

CLEs for zkAutomation can be built from scratch, migrated from CLEs for zkIndexing or existing subgraphs, or by reusing deployed ones. If developers choose to migrate from an existing CLE for zkIndexing, they only need to change the Meta App type of that CLE to make it a valid source for zkAutomation.

Once the zkAutomation job has been registered (and the CLE has been optionally deployed), the corresponding zkAutomation service will start and automation jobs will be executed when the trigger condition is met.
