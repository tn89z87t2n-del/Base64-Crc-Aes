# Base64-Crc-Aes

Verifikačný nástroj pre prenos dát na **MSP430FR5969**. Jeden samostatný
`index.html` (HTML+CSS+JS, žiadny build) — otvoríš dvojklikom, funguje offline.

Pomáha overiť každý krok, ktorým prechádzajú dáta pri odosielaní z firmvéru:
kódovanie, kontrolný súčet/parita a AES šifrovanie. Všade je zobrazenie v
**DEC / HEX / BIN (+ ASCII)**.

## Funkcie

- **Pipeline** — zadáš dáta raz, tečú cez zapnuteľné kroky (AES → CRC → Base64),
  každý medzikrok vidíš vo všetkých formátoch. Kroky sa dajú presúvať a vypínať.
- **Base / kódovanie** — Base64 (štandard + URL-safe), Base32, Base16/Hex, padding on/off.
- **CRC / Parita / Hamming**
  - CRC 8/16/32 s plnou konfiguráciou (poly, init, refin, refout, xorout) a presetmi
    vrátane **MSP430 CRC16 — CRCDI** (≡ CRC-16/MCRF4XX) a **CRCDIRB** (≡ CRC-16/CCITT-FALSE).
  - Parita even/odd, per-bajt (UART) aj cez celú správu.
  - Hamming(7,4) a Hamming(12,8), voliteľne SECDED.
- **AES** — 128/192/256, režimy ECB (HW natívny), CBC, CTR, CFB, OFB, šifrovanie aj
  dešifrovanie, blok po bloku. Padding none / PKCS#7 / zero.
- **MSP430 info** — vysvetlenie periférií FR5969 (CRC16, AESA, UART, endianness).

UI je dvojjazyčné **SK/EN** (default SK) s prepínačom **dark/light** (default dark).

## Použitie

Otvor `index.html` v prehliadači. Indikátor `self-test ✓` v hlavičke potvrdzuje,
že AES (FIPS-197 vektory) a CRC (známe kontrolné hodnoty) počítajú správne.
