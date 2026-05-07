# Patch Note — 08 Mei 2026

## Infrastruktur baru
REDIS
- **Port**: `127.0.0.1:6379`

### Perubahan
- Hapus Semua metode yang dipakai websocket
- Semua realtime system sekarang memakai Redis
- Improve performance handling request
- Reduce idle connection usage
- Better stability untuk multiple bot

---

## 1. Session & System
- [x] `GET /telebot/mysession`
    - **Params:** `apikey`
    - **Returns:** Array of all connected bots.

- [x] `GET /telebot/setting`
    - **Params:** `apikey`, `botname`
    - **Returns:** Contents of `settingBot.json` and `listConf.json`.

---

## 2. Product Management (SQLite)
- [x] `GET /telebot/getlist`
    - **Params:** `apikey`, `botName`, `page`

- [x] `GET /telebot/getitem`
    - **Params:** `apikey`, `botname`, `idbarang`

- [x] `POST /telebot/edititem`
    - **Body:** `method`, `apikey`, `botname`, `idbarang`, `text`

    - **Methods:**
        - `updatedesc`
        - `updatetitle`
        - `updateharga`
        - `updatesnk`
        - `updatecategory`

---

## 3. User Management (JSON)
- [x] `GET /telebot/listuser`
    - **Params:** `apikey`, `botname`, `page`

- [x] `GET /telebot/getuser`
    - **Params:** `apikey`, `botname`, `userid`

- [x] `POST /telebot/userupdate`
    - **Body:** `method`, `apikey`, `botname`, `userid`, `text`

    - **Methods:**
        - `addsaldo`
        - `takesaldo`
        - `ubahname`
        - `whitelist`

---

## 4. Category & Vouchers (JSON)

### Category
- [x] `GET /telebot/listcategory`
    - **Params:** `apikey`, `botname`, `page`

- [x] `POST /telebot/managecategory`
    - **Body:** `method`, `apikey`, `botname`, `categoryName`, `value`

    - **Methods:**
        - `addcategory`
        - `deletecategory`
        - `renamecategory`

### Voucher
- [x] `GET /telebot/getvoucher`
    - **Params:** `apikey`, `botname`, `page`

- [x] `POST /telebot/managevoucher`
    - **Body:** `method`, `apikey`, `botname`, `kodevoucher`, `persen`, `limit`, `expiredat`

    - **Methods:**
        - `addvoucher`
        - `changevoucher`
        - `deletevoucher`
