# Steganography

```bash
# Install StegHide tool
sudo apt install steghide

# Hide a secret into a picture (pic.jpg will be replaced)
steghide embed -cf pic.jpg -ef secret.txt

# Display info about a file whether it has embedded secrets
steghide info pic.jpg

# Extract secret from a picture
steghide extract -sf pic.jpg
```

## References

[Steganography - A list of useful tools and resourcesPermalink](https://0xrick.github.io/lists/stego/)

[Steghide Documentation](https://steghide.sourceforge.net/)