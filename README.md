# SPA mau de test GTM (DEV_MIERUCA_HEAT_OPT-9501)

Chi dung de test, tach biet voi code san pham.

## Cac man hinh (route)
| URL | screen_name |
|---|---|
| `/` | `home` |
| `/products` | `product_list` |
| `/products/1` ... `/products/4` | `product_detail` |
| `/contact` | `contact` |
| URL khac | `not_found` |

## dataLayer event
Moi lan doi man hinh (ke ca lan tai dau tien):

```js
{
  event: 'screen_change',
  screen_name: 'product_list',
  page_path: '/products',
  page_title: '...',
  previous_path: '/',
  navigation_type: 'initial' | 'push' | 'popstate'
}
```

## Che do router
- `path` (mac dinh khi chay qua http/https): URL dang `/products`, can server hoac Vercel (da co `vercel.json`).
- `hash`: URL dang `#/products`. Tu dong bat khi mo file truc tiep (`file://`), hoac them `?router=hash` vao URL.
- `page_path` trong dataLayer luon la duong dan logic (`/products`) o ca 2 che do.

## Cai dat
1. Thay `GTM-XXXXXXX` bang container ID that (2 cho trong `index.html`).
2. Deploy len Vercel (`vercel.json` da co rewrite ve `index.html` de F5 / vao thang `/products` khong bi 404).
3. Them `?debug=0` vao URL de an panel debug.

## Cau hinh trong GTM
- Trigger: loai Custom Event, ten event `screen_change`.
- (Tuy chon) Data Layer Variable: `screen_name`, `page_path`, `navigation_type`.
- Gan tag tracking cua cong ty vao trigger do. De test viec tag KHONG chay o lan tai dau, dung trigger khac thay cho "All Pages / Initialization".
