

### 1. Session & System
- [x] `GET /telebot/mysession`
    - **Params:** `apikey`
    - **Returns:** Array of all connected bots.
- [x] `GET /telebot/setting`
    - **Params:** `apikey`, `botname`
    - **Returns:** Contents of `settingBot.json` and `listConf.json`.

### 2. Product Management (SQLite)
- [x] `GET /telebot/getlist`
    - **Params:** `apikey`, `botName`, `page`
- [x] `GET /telebot/getitem`
    - **Params:** `apikey`, `botname`, `idbarang`
- [x] `POST /telebot/edititem`
    - **Body:** `method`, `apikey`, `botname`, `idbarang`, `text`
    - **Methods:** `updatedesc`, `updatetitle`, `updateharga`, `updatesnk`, `updatecategory`

### 3. User Management (JSON)
- [x] `GET /telebot/listuser`
    - **Params:** `apikey`, `botname`, `page`
- [x] `GET /telebot/getuser`
    - **Params:** `apikey`, `botname`, `userid`
- [x] `POST /telebot/userupdate`
    - **Body:** `method`, `apikey`, `botname`, `userid`, `text`
    - **Methods:** `addsaldo`, `takesaldo`, `ubahname`, `whitelist`

### 4. Category & Vouchers (JSON)
- [x] `GET /telebot/listcategory`
    - **Params:** `apikey`, `botname`, `page`
- [x] `POST /telebot/managecategory`
    - **Body:** `method`, `apikey`, `botname`, `categoryName`, `value`
    - **Methods:** `addcategory`, `deletecategory`, `renamecategory`
- [x] `GET /telebot/getvoucher`
    - **Params:** `apikey`, `botname`, `page`
- [x] `POST /telebot/managevoucher`
    - **Body:** `method`, `apikey`, `botname`, `kodevoucher`, `persen`, `limit`, `expiredat`
    - **Methods:** `addvoucher`, `changevoucher`, `deletevoucher`

---

## 🛠️ Infrastructure Technical Specs
- **Bridge Type**: Thread-safe RESP Emulator (`redis_bridge.go`)
- **Write Method**: Atomic TCP Socket Write (`c.NetConn().Write`)
- **Broadcast Mode**: 2.0s collection window for multi-bot responses.
- **Port**: `127.0.0.1:6379`
