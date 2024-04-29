---
description: >-
  Add new data source (other than on-chain event or storage) to CLE with Data
  Source Plugin
---

# Bring Your Own Data Source

### Data Source Plugin

Data Source Plugin is a generalized plugin interface designed for CLE infrastructure development. DSP is designed for adding new data source support.

DSP primarily designed to assist in CLE core development (e.g. by the ORA Team), rather than application development by CLE Dev Users.

### Add new data source with DSP

{% hint style="info" %}
If you only need to add new data as a (one time use only) data source, then you can actually add the specific data directly to `mapping.ts`.
{% endhint %}

If you want to add a new data source to CLE, you need to implement the DSP interface and provide implementation.

#### a) Interface of DSP

DSP is dependent on the CLE lifecycle of execution, proving, and on-chain verification.

* `cle-api`: the entrance of all DSP, `dsphub` records all the available DSPs.
* `cle-lib`: the provable wasm part, defines how to read data and calls the dsp-specific handle function in the proving stage.
* `Factory Contract`: the verifier part, defines how to verify a DSP-specific CLE trigger tx on-chain.

#### b) Develop a DSP

Follow the interface section to implement every components, or re-use other dsp’s code.

* API:
  * defines execParams / proveParams
  * implement a customized DataPrep
  * implement a child DSP class that extends DSP class
  * register this DSP class by `dspHub.setDSP` in `src/dsp/hub`
* Lib:
  * add a new dir (name should be fit with the dsp Hub Key)
  * implement and export `asmain_lib`, `zkmain_lib` and `registerHandle` in `index.ts`
  * export other types that might be used in CLE mappings
* Contract:
  * deploy a DSP Verifier contract and set the address to the CLE Factory
