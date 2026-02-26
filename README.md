# ✨ React Confirm Animated Modal

A lightweight and customizable confirm modal for React with a built-in loading spinner for async actions.

Perfect for:

* Delete confirmations
* Form submissions
* API actions
* Critical user decisions

No Tailwind.
No UI libraries.
No Radix dependency.
Just plug & play...

---

## 📦 Installation

```bash
npm install @amirhpooladi/react-confirm-modal
```

---

## 🚀 Usage

```tsx
"use client"

import { useState } from "react"
import { ConfirmModal } from "@amirhpooladi/react-confirm-modal"
import "@amirhpooladi/react-confirm-modal/dist/index.css"

export default function Example() {
  const [open, setOpen] = useState(false)
  const [loading, setLoading] = useState(false)

  const handleConfirm = async () => {
    setLoading(true)

    await new Promise(res => setTimeout(res, 2000))

    setLoading(false)
    setOpen(false)
  }

  return (
    <>
      <button onClick={() => setOpen(true)}>
        Delete Item
      </button>

      <ConfirmModal
        open={open}
        onCancel={() => setOpen(false)}
        onConfirm={handleConfirm}
        isLoading={loading}
        title="Delete this item?"
        description="This action cannot be undone."
        confirmLabel="Delete"
        cancelLabel="Cancel"
        type="delete"
      />
    </>
  )
}
```

---

## ⚙️ Props

| Prop         | Type                 | Default         | Description               |
| ------------ | -------------------- | --------------- | ------------------------- |
| open         | boolean              | —               | Controls modal visibility |
| onConfirm    | () => void           | —               | Confirm action            |
| onCancel     | () => void           | —               | Cancel action             |
| title        | string               | "Are you sure?" | Modal title               |
| description  | string               | —               | Optional description      |
| confirmLabel | string               | "Confirm"       | Confirm button text       |
| cancelLabel  | string               | "Cancel"        | Cancel button text        |
| isLoading    | boolean              | false           | Shows spinner             |
| type         | "default" | "delete" | "default"       | Button style              |

---

## 🎨 Button Types

```tsx
type="default"
type="delete"
```

---

## 🧠 Async Friendly

Modal stays open automatically while your async action is loading:

```tsx
const handleConfirm = async () => {
  setLoading(true)
  await deleteUser()
  setLoading(false)
  setOpen(false)
}
```

---

## 📌 Notes

You must import the styles manually:

```ts
import "@amirhpooladi/react-confirm-modal/dist/index.css"
```

---

## 🪪 License

MIT
