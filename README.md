# Git & Next.js Pratik Eğitimi

## Amaç

Bu çalışma kapsamında katılımcıların aşağıdaki konulara pratik olarak giriş yapması hedeflenmektedir:

- Git ve GitHub workflow
- Proje yönetimi
- Next.js ile frontend geliştirme
- Routing mantığı
- React hook yapısı
- State management
- Tailwind ile basit UI geliştirme

Bu çalışma yüzeysel fakat uygulamalı bir giriş niteliğindedir. Katılımcıların bazı konuları AI ve internet üzerinden araştırarak öğrenmesi beklenmektedir.

## 1. Gerekli Kurulumlar

### 1.1 Node.js

Node.js kurulmalıdır.

İndirme adresi:  
https://nodejs.org/en

Kurulum kontrolü:

```bash
node -v
npm -v
```

### 1.2 Git

Git kurulmalıdır.

Kurulum kontrolü:

```bash
git --version
```

### 1.3 GitHub Hesabı

Herkes kendi GitHub hesabını bana iletecek.  
Ben kullanıcıları aşağıdaki repoya ekleyeceğim:

```bash
git@github.com:samilcdemir/esoes-hsd-core-team.git
```

Repo erişimi sağlandıktan sonra davet kabul edilecektir.

## 2. SSH Ayarı

GitHub ile SSH bağlantısı kurulacaktır.

### SSH key oluşturma

```bash
ssh-keygen -t ed25519 -C "mail@example.com"
```

### Public key görüntüleme

```bash
cat ~/.ssh/id_ed25519.pub
```

Bu anahtar GitHub hesabında şu bölüme eklenecek:

`Settings → SSH and GPG Keys`

### Bağlantı testi

```bash
ssh -T git@github.com
```

## 3. Repo Klonlama

Repo bilgisayara indirilecektir.

```bash
git clone git@github.com:samilcdemir/esoes-hsd-core-team.git
```

## 4. Kendi Next.js Projesini Oluşturma

Repo içerisinde herkes kendi adına bir Next.js projesi oluşturacaktır.

### Örnek proje isimleri

- `ertaylan-nextjs-init`
- `ahmet-nextjs-init`
- `ayse-nextjs-init`

### Next.js proje oluşturma

```bash
npx create-next-app@latest proje-adi
```

Önerilen seçenekler:

- TypeScript: isteğe bağlı
- Tailwind: evet
- App Router: evet
- ESLint: evet

Proje çalıştırma:

```bash
npm run dev
```

## 5. Projeyi Repoya Yükleme

Projeyi oluşturduktan sonra repoya yüklenmelidir.

```bash
git add .
git commit -m "initial nextjs project"
git push
```

## 6. Projede Yapılacaklar

En az 2 sayfa olacak.

Örnek:

- `/form`
- `/profile`

## 7. Form Sayfası

Bir sayfada form oluşturulacaktır.

Formda aşağıdaki bilgiler alınabilir:

- isim
- yaş
- şehir
- hobiler
- kısa biyografi

Butona basıldığında girilen bilgiler ekranda gösterilecektir.

### Araştırılması önerilen konular

- React form yönetimi
- `useState`
- controlled components
- event handling

## 8. Zustand ile State Management

Projeye Zustand paketi kurulacaktır.

```bash
npm install zustand
```

### Beklenen yapı

#### Sayfa 1

Form verisi girilecek.

#### Sayfa 2

Girilen veriler global state üzerinden gösterilecek.

Amaç: React state management mantığını anlamak.

## 9. Hook Mantığı

Aşağıdaki hook'lar araştırılmalıdır:

- `useState`
- `useEffect`
- `useMemo`
- `useCallback`
- `useRef`

Ayrıca şu kavramlar incelenmelidir:

- React component lifecycle
- dependency array
- rerender mantığı

## 10. Next.js Routing

Next.js routing sistemi araştırılmalıdır.

Özellikle şu konular incelenebilir:

- App Router
- `Link` kullanımı
- nested route
- navigation
- route segment mantığı

## 11. Tailwind CSS Kullanımı

Projede Tailwind kullanılacaktır.

Amaç:

- temel layout
- kart tasarımı
- buton stilleri
- spacing kullanımı
- responsive yaklaşım

## 12. Kişisel Tanıtım Sayfası

Projeye bir kişisel tanıtım sayfası eklenebilir.

İçerik örneği:

- isim
- kısa tanıtım
- hobiler
- sevilen teknolojiler
- hedefler

Amaç: Frontend tasarım mantığını görmek.

## 13. Git Kullanımı

Beklentiler:

- anlamlı commit mesajları
- düzenli commit
- repo düzeni
- gereksiz dosyaların repoya eklenmemesi

### Commit örnekleri

- `feat: add nextjs project`
- `feat: create form page`
- `feat: add zustand store`
- `style: improve profile page ui`

## 14. Araştırma Önerileri

Bu çalışma sırasında bazı konuların AI veya internet üzerinden araştırılması beklenmektedir.

Önerilen araştırma başlıkları:

- `nextjs app router nedir`
- `react useState nasıl çalışır`
- `react useEffect lifecycle`
- `zustand state management nedir`
- `nextjs routing nasıl çalışır`
- `tailwind css layout nasıl yapılır`
- `react form management`

## 15. Önerilen Kaynaklar

### Resmi dokümantasyonlar

- Next.js  
  https://nextjs.org/docs
- React  
  https://react.dev
- Zustand  
  https://docs.pmnd.rs/zustand/getting-started/introduction
- Tailwind  
  https://tailwindcss.com/docs

## 16. Örnek Next.js Proje İskeleti

Aşağıdaki yapı önerilebilir:

```text
my-nextjs-app
app
├ page.tsx
├ layout.tsx
├ form
│ └ page.tsx
└ profile
  └ page.tsx
components
├ Form.tsx
└ ProfileCard.tsx
store
└ userStore.ts
styles
└ globals.css
```

## 17. Örnek Zustand Store

`store/userStore.ts`

```ts
import { create } from "zustand"

export const useUserStore = create((set) => ({
  user: null,
  setUser: (data) => set({ user: data }),
}))
```

## 18. Örnek Form Component

```tsx
"use client"

import { useState } from "react"
import { useUserStore } from "@/store/userStore"

export default function FormPage() {
  const setUser = useUserStore((state) => state.setUser)
  const [name, setName] = useState("")
  const [city, setCity] = useState("")

  const submit = () => {
    setUser({ name, city })
  }

  return (
    <div>
      <input
        placeholder="Name"
        onChange={(e) => setName(e.target.value)}
      />
      <input
        placeholder="City"
        onChange={(e) => setCity(e.target.value)}
      />
      <button onClick={submit}>Submit</button>
    </div>
  )
}
```

## 19. Hedef

Bu çalışma sonunda katılımcıların aşağıdaki konular hakkında pratik bir farkındalık kazanması beklenmektedir:

- Git workflow
- GitHub repo yönetimi
- Next.js proje yapısı
- Routing mantığı
- React hook yapısı
- State management
- Basit frontend UI geliştirme

# hsd-core-team-front-end
