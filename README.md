# Building & Downloading the IPA

Automated GitHub Actions workflow to build a Switch game into a native iOS app (`.ipa`) using your private Hugging Face dataset.

---

## 1. Prerequisites

Before running the workflow, make sure you have:
* **Switch Keys:** Your `prod.keys` file.
* **Game Files:** Your base game `.nsp` (and optional update `.nsp`) uploaded to a **Private Dataset** on [Hugging Face](https://huggingface.co/).
* **HF Token:** A `Read` access token generated from **Hugging Face** → **Settings** → **Access Tokens**.

---

## 2. Set Up GitHub Secrets

The build runner needs your keys and access token to pull the files securely.

1. Go to your repository's **Settings** → **Secrets and variables** → **Actions**.
2. Click **New repository secret** and add:
   * **Name:** `HF_TOKEN`  
     **Secret:** Paste your Hugging Face Read token (`hf_...`).
3. Click **New repository secret** again and add:
   * **Name:** `PROD_KEYS`  
     **Secret:** Paste the entire plain-text contents of your `prod.keys` file.

---

## 3. Trigger the Build

1. Go to the **Actions** tab in this repository.
2. In the left sidebar, select the **Build nxnative IPA** workflow.
3. Click the **Run workflow** dropdown on the right and fill in the parameters:
   * **Hugging Face Dataset Repo:** `your-username/dataset-name` (e.g., `alex/switch-games`).
   * **Base game filename:** The base game filename on Hugging Face (e.g., `base.nsp`).
   * **Update filename:** *(Optional)* The update filename (e.g., `update.nsp`). Leave empty if compiling base-only.
4. Click **Run workflow**.

> Extraction, shader translation, and code generation typically take **10 to 25 minutes**.

---

## 4. Download the IPA

1. When the run finishes with a green checkmark, click into the run details.
2. Scroll to the bottom to the **Artifacts** section.
3. Click **`compiled-ipa`** to download the archive through your browser.
4. Open the downloaded zip with **7-Zip** or **WinRAR** to extract your `.ipa`.

---

## 5. Sideloading Notice

> **Use Sideloadly to install the `.ipa` onto your device.**  
> Other sideloading tools (such as AltStore or basic free managers) will likely fail or time out due to the large binary footprint, custom entitlements, and payload size of recompiled games.
