# **Cifrado y Descifrado con DES, 3DES y AES**

Este laborartorio implementa el cifrado y descifrado de datos utilizando los algoritmos **DES (ECB), 3DES (CBC) y AES (ECB y CBC)** en Python. También incluye pruebas unitarias para validar la correcta funcionalidad de cada cifrado y descifrado.

---

##  Características
- Implementación de **DES en ECB**, **3DES en CBC**, **AES en ECB y CBC**.
- Generación **segura** de claves aleatorias y vectores de inicialización (IV).
- Uso de **relleno (padding)** automático y manual donde es requerido.
- **Pruebas unitarias** que verifican la integridad del cifrado y descifrado.
- Reflexión sobre **los riesgos de los PRNGs débiles en criptografía**.

---



## **Instalación y Requisitos**
Este proyecto usa la librería `pycryptodome`. Para instalarla:
```bash
pip install pycryptodome
```

Asegúrate de estar usando **Python 3.7 o superior**.

---

## ** Uso del Código**
### **Ejemplo de Ejecución del Cifrado y Descifrado**
```python
from Crypto.Cipher import DES, DES3, AES
from Crypto.Util.Padding import pad, unpad
from Crypto.Random import get_random_bytes

mensaje = "Hola, este es un mensaje secreto!"
clave = get_random_bytes(8)  # Clave para DES

# Cifrado con DES en ECB
cipher = DES.new(clave, DES.MODE_ECB)
ciphertext = cipher.encrypt(pad(mensaje.encode(), DES.block_size))

decipher = DES.new(clave, DES.MODE_ECB)
decrypted_text = unpad(decipher.decrypt(ciphertext), DES.block_size).decode()

print("Texto cifrado:", ciphertext.hex())
print("Texto descifrado:", decrypted_text)
```

---

##
**Pruebas incluidas:**
- **DES en ECB**: Valida que el descifrado es correcto.
- **3DES en CBC**: Verifica la integridad del texto descifrado.
- **AES en ECB y CBC**: Confirma que el cifrado y descifrado son consistentes.

---
