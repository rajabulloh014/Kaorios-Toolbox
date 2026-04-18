# Kaorios Toolbox Patch Guide

This guide explains the smali changes needed to import and use the Kaorios Toolbox hook classes.

## Framework.jar

Import the KaoriosToolbox DEX classes into `Framework.jar`.

### 1) `Landroid/app/Application;`

**Method:** `attach(Landroid/content/Context;)V`

Add the following line immediately after:

```smali
invoke-virtual {p0, p1}, Landroid/app/Application;->attachBaseContext(Landroid/content/Context;)V
```

```smali
invoke-static {p1}, Landroid/security/kaorios/KaoriosHook;->initContext(Landroid/content/Context;)V
```

---

### 2) `Landroid/app/ApplicationPackageManager;`

**Method:** `hasSystemFeature(Ljava/lang/String;I)Z`

Add the following code below `.registers X`:

```smali
invoke-static {p1, p2}, Landroid/security/kaorios/KaoriosHook;->hasSystemFeature(Ljava/lang/String;I)Ljava/lang/Boolean;
move-result-object v0

if-eqz v0, :cond_kaorios
invoke-virtual {v0}, Ljava/lang/Boolean;->booleanValue()Z
move-result v0
return v0

:cond_kaorios
```

---

### 3) `Landroid/security/keystore2/AndroidKeyStoreKeyPairGeneratorSpi;`

**Method:** `generateKeyPair()Ljava/security/KeyPair;`

Add the following code below `.registers X`:

```smali
invoke-static {p0}, Landroid/security/kaorios/KaoriosHook;->initGenerateSoftwareKeyPair(Ljava/lang/Object;)Ljava/security/KeyPair;
move-result-object vX

if-eqz vX, :cond_kaorios
return-object vX

:cond_kaorios
```

#### Register note

In this method, pay attention to `.registers X`.

- Increase the current register count by `1`
- Replace `vX` with the register number at `registers - 2`

Example:

- If the method originally uses `15` registers
- Change it to `16` registers
- Then change `vX` to `v14`

---

### 4) `Landroid/security/keystore2/AndroidKeyStoreSpi;`

**Method:** `engineGetCertificateChain(Ljava/lang/String;)[Ljava/security/cert/Certificate;`

Find this part:

```smali
const/4 vA, 0x0
aput-object vB, vC, vA
return-object vD
```

Add the following code below:

```smali
const/4 vA, 0x0
aput-object vB, vC, vA

invoke-static {vC}, Landroid/security/kaorios/KaoriosHook;->CertificateChainIfNeeded([Ljava/security/cert/Certificate;)[Ljava/security/cert/Certificate;
move-result-object vD
```

#### Note

`move-result-object vD` is the value returned by `return-object vD`.

Also, in `invoke-static {vC}`, the array register `vC` is the same register used by `aput-object vB, vC, vA`.

#### Example

```smali
const/4 v4, 0x0
aput-object v2, v3, v4

invoke-static {v3}, Landroid/security/kaorios/KaoriosHook;->CertificateChainIfNeeded([Ljava/security/cert/Certificate;)[Ljava/security/cert/Certificate;
move-result-object v3

return-object v3
```

---

## Services.jar

### 1) `Lcom/android/server/SystemServer;`

**Method:** `run()V`

Add the following line before:

```smali
Lcom/android/server/SystemServer;->startOtherServices(Lcom/android/server/utils/TimingsTraceAndSlog;)V
```

```smali
invoke-static {}, Landroid/security/kaorios/KaoriosHook;->initSystemServer()V
```

---

## Register naming convention

To keep the guide easy to read, use the same formatting for registers that refer to the same value.

For example:

- `v0` = returned Boolean in `hasSystemFeature`
- `vD` = return value in `engineGetCertificateChain`
- `vX` = temporary result register in `generateKeyPair`

This makes it easier to track which register is used as input, output, or temporary storage.

## Summary

- `Framework.jar`: hook `Application`, `ApplicationPackageManager`, and `keystore2`
- `Services.jar`: hook `SystemServer`
- Adjust register counts carefully when adding new instructions
- Keep register usage consistent inside each method
