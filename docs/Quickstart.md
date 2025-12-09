# ⭐ SSM-ENCRYPT — Quickstart Guide

**Deterministic • Tiny • Offline • Post-Decryption-Safe Encryption**  
*(HTML-Only Edition — LAW 0SE compliant)*

---

## **1. Requirements**

No installation required.  
SSM-Encrypt runs as a single self-contained HTML file.

- No Python  
- No packages  
- No backend  
- No randomness  
- No network access  

Everything operates 100% offline, deterministic, and reproducible.

If your machine has a browser, it can run SSM-Encrypt.  
Just double-click the HTML file.

---

## **2. Recommended Folder Structure**

/SSM-Encrypt  
  SSM-Encrypt.html — Complete working demo (Sender + Receiver)  
  Demo_SSM-Encrypt.mp4 — Walkthrough video demonstration  

  Concept-Flyer_SSM-Encrypt_ver2.3.pdf — Five-page conceptual overview  
  Brief-SSM-Encrypt_ver2.3.pdf — Condensed summary document  
  SSM-Encrypt_ver2.3.pdf — Full detailed architecture  

  Example.md — Real structural bundle example  
  FAQ.md — Frequently Asked Questions  
  Quickstart.md — This guide  

All files are self-contained and run offline.

## **3. Running the Demo (HTML Edition)**

Open:

**SSM-Encrypt.html**

The interface contains two panels:

---

### **Sender Panel**

- Plaintext message  
- Message Passphrase (Show/Hide)  
- Master Password (Show/Hide)  
- **Encrypt** button  
- Bundle output (CIPHER, PREV, STAMP, AUTH fields, MANIFEST)  
- Structural Trace (PREV, sha256(cipher), AUTH_MSG)

**Important:**  
The bundle does not contain plaintext.  
Only structural fields are transported.

---

### **Receiver Panel**

- Bundle input box (copy from Sender)  
- Passphrase (Show/Hide)  
- Master Password (Show/Hide)  
- **Decrypt** button  
- Result panel (VALID / COLLAPSE)  
- Explicit **CAUSE** field

---

### **How to run one full cycle**

#### **1️⃣ Encrypt**

Enter:  
- plaintext  
- passphrase  
- master password  

Press **Encrypt**.

This produces a structural bundle containing:

- CIPHER  
- PREV  
- STAMP  
- AUTH_MSG  
- AUTH_MASTER  
- ID_STAMP  
- MANIFEST

**Note:**  
PLAINTEXT is not included in the bundle.

The Structural Trace shows the raw continuity components:

- PREV  
- sha256(cipher)  
- AUTH_MSG

---

#### **2️⃣ Transfer**

Copy the bundle manually into the receiver panel.

Enter:  
- passphrase  
- master password

---

#### **3️⃣ Decrypt**

Press **Decrypt**.

If continuity, authentication, and device correlation align:

**VALID — Bundle accepted and consumed.**  
PLAINTEXT: \<message\>  
CAUSE: NONE

Plaintext appears only in the result panel, not inside the bundle.

If anything diverges:

**COLLAPSE**  
CAUSE: \<deterministic reason\>

This demonstrates:

- deterministic structural validation  
- dual authentication  
- device correlation  
- one-time decryption guarantees

## **3A. Interface Characteristics for Precision Testing**

### **Show/Hide Controls**

Secret fields offer visibility toggles to prevent mistakes while preserving discretion.

---

### **Structural Trace Display**

Shows the exact continuity equation inputs:

(continuity formula provided separately below)

- PREV  
- sha256(cipher)  
- AUTH_MSG

---

### **CAUSE Reporting**

Every collapse clearly states its deterministic origin:

- AUTH_MSG  
- AUTH_MASTER  
- CONTINUITY  
- POST-DECRYPTION  
- MISSING_SECRETS  

LAW 0SE principle:  
**“Every failure must collapse with an explicit structural cause.”**

---

### **Color Feedback**

- **VALID** → green  
- **COLLAPSE** → red  
- **CAUSE** → blue  

---

### **Manual Transfer Flow**

Bundles are copy–paste transferred to preserve deterministic control.
```
stamp_n = sha256( stamp_(n-1) + sha256(cipher_n) + auth_msg_n )
```

## **4. Important Testing Behavior (Shared Browser Continuity)**

Sender and receiver operate inside:

- the same browser  
- the same memory  
- the same continuity chain  
- the same device identity  

Therefore:

**First decryption → VALID**  
**Second attempt with the same bundle → COLLAPSE**

This demonstrates:

- forward-only structural progression  
- irreversible continuity  
- one-time validity  

On different devices or profiles, each has its own chain.

## **4A. One-Time Decryption and Message Recovery**

After a correct decrypt:

- stamp is consumed  
- continuity advances  
- bundle becomes invalid forever  

If the receiver loses the plaintext due to:

- refresh  
- close  
- crash  
- shutdown  
- failure to copy  

…it cannot be recovered from the consumed bundle.

**Correct action:**  
Request the sender to issue a new bundle.

This ensures perfect replay protection.

## **5. What SSM-Encrypt Actually Does (Technical Summary)**

SSM-Encrypt applies two deterministic symbolic layers:

---

### **A. T-Lane Structural Transform (Cipher Layer)**

A reversible symbolic mapping:

(cipher formula provided separately below)

- deterministic  
- reversible  
- no randomness  
- no IVs  

---

### **B. Continuity Stamp — LAW 0SE**

(continuity formula provided separately below)

Where:

- STAMP_(n-1) enforces ordering  
- sha256(cipher) enforces uniqueness  
- AUTH_MSG enforces structural integrity  

---

### **Important Note**

The plaintext is never included in the transported bundle.  
Only cipher and structural fields move across Sender → Receiver.

A bundle is valid only once, at the moment continuity aligns.  
Any mismatch → **COLLAPSE**.

**Cipher Transform Formula**
```
cipher[i] = transform( plaintext[i], passphrase, i )
```

**Continuity Formula**
```
STAMP_n = sha256( STAMP_(n-1) + sha256(cipher) + AUTH_MSG )
```

## **6. Troubleshooting (Deterministic Failure Modes)**

❗ **COLLAPSE: Continuity mismatch**  
The bundle was already consumed.  
Continuity cannot go backward.

❗ **AUTH_MSG failure**  
Incorrect message passphrase.

❗ **AUTH_MASTER failure**  
Incorrect master password OR device mismatch.

❗ **POST-DECRYPTION failure**  
The bundle was already consumed on a previous valid decryption.  
Replay is structurally impossible.

❗ **ID binding failure**  
Browser-local device identity mismatch.

Prevents:  
- forwarding  
- relay attacks  
- cross-device replay

## **7. Resetting the Demo**

The **Reset Demo** button clears:

- input fields  
- UI state  

…and resets the deterministic continuity environment.

A full browser restart resets:

- prev_stamp  
- device_id  
- sender state  
- receiver state  

Use this to begin a fresh set of validation cycles.

## **8. Recommended Structural Experiments**

To understand LAW 0SE via hands-on testing:

- Change one character in the passphrase → **collapse**  
- Change one character in the master password → **collapse**  
- Attempt a second decryption → **collapse**  
- Encrypt two messages with the same keys → different stamp and cipher  
- Restart browser → continuity resets → messages validate again  

Each experiment highlights a distinct structural law.
