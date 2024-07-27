def caesar_cipher_encrypt(text, shift):
    result = ""
    for char in text:
        if char.isalpha():
            # Determine if the character is uppercase or lowercase
            start = ord('A') if char.isupper() else ord('a')
            # Shift character and wrap around using modulo
            shifted = chr(start + (ord(char) - start + shift) % 26)
            result += shifted
        else:
            result += char
    return result

def caesar_cipher_decrypt(text, shift):
    return caesar_cipher_encrypt(text, -shift)

def main():
    print("Caesar Cipher Encryption/Decryption")
    choice = input("Do you want to (e)ncrypt or (d)ecrypt a message? ").lower()
    if choice not in ['e', 'd']:
        print("Invalid choice!")
        return
    
    message = input("Enter the message: ")
    shift = int(input("Enter the shift value: "))
    
    if choice == 'e':
        encrypted_message = caesar_cipher_encrypt(message, shift)
        print(f"Encrypted message: {encrypted_message}")
    elif choice == 'd':
        decrypted_message = caesar_cipher_decrypt(message, shift)
        print(f"Decrypted message: {decrypted_message}")

if __name__ == "__main__":
    main()
    
