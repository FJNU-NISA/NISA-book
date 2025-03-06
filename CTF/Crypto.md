# Crypto - 密码学

密码学是网络安全和 CTF 竞赛中的重要领域，涵盖了对称加密、非对称加密、哈希函数、数字签名等多种技术。以下是对密码学部分的完善和内容填充。

## 非对称加密

非对称加密使用一对密钥（公钥和私钥）进行加密和解密，常见的算法包括 RSA、ECC 等。

### RSA

- **原理**：基于大整数分解的困难性，公钥用于加密，私钥用于解密。
- **关键参数**：
  - **n**：模数，由两个大素数 $p$ 和 $q$ 相乘得到，即 $n = p \times q$。
  - **e**：公钥指数，通常为 65537。
  - **d**：私钥指数，满足 $e \times d \equiv 1 \mod \phi(n)$，其中 $\phi(n) = (p-1)(q-1)$。
- **加密过程**：密文  $c = m^e \mod n$。
- **解密过程**：明文 $m = c^d \mod n$。
- **常见攻击**：
  - **小公钥指数攻击**：当 $e$ 很小时，可能通过低加密指数攻击恢复明文。
  - **共模攻击**：当多个密文使用相同的 $n$ 时，可能通过共模攻击恢复明文。
  - **因数分解攻击**：当 $n$ 可以被分解时，破解 RSA。
- **工具**：
  - `yafu`：用于大整数分解。
  - `RsaCtfTool`：用于自动化 RSA 攻击。

## 常用环境

密码学研究中常用的工具和库包括：

### yafu

- **用途**：用于大整数分解，支持多种分解算法（如 ECM、QS）。
- **示例**：
  
  ```bash
  yafu "factor(123456789)"
  ```

### gmpy2

- **用途**：Python 的高精度数学库，支持大整数运算、模运算等。
- **示例**：
  
  ```python
  import gmpy2
  n = gmpy2.mpz(123456789)
  p = gmpy2.next_prime(n)
  ```

### pycryptodome

- **用途**：Python 的密码学库，支持对称加密、非对称加密、哈希函数等。
- **示例**：
  
  ```python
  from Crypto.Cipher import AES
  cipher = AES.new(key, AES.MODE_ECB)
  plaintext = cipher.decrypt(ciphertext)
  ```

### libnum

- **用途**：Python 的密码学工具库，支持 RSA、离散对数、模运算等。
- **示例**：
  
  ```python
  import libnum
  p = libnum.generate_prime(1024)
  ```

### Sage

- **用途**：基于 Python 的数学计算系统，支持高级数学运算和密码学分析。
- **示例**：
  
  ```python
  n = 123456789
  factor(n)
  ```

---

## 实践与练习

1. **RSA 加密与解密**：使用 `pycryptodome` 实现 RSA 加密和解密。
2. **大整数分解**：使用 `yafu` 分解一个大整数。
3. **RSA 攻击**：使用 `RsaCtfTool` 对给定的 RSA 参数进行攻击。
4. **模运算**：使用 `gmpy2` 计算大整数的模逆。
