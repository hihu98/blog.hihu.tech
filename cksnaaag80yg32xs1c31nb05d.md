## Tại sao app Nextjs của mình lại hot-reload chậm thế nhỉ?

Gần đây, mình đang làm việc trên một dự án mới của công ti, do mình setup từ đầu. Mình sử dụng boilerplate `create-next-app` của Nextjs để khởi tạo dự án. Ngoài ra, mình có sử dụng Tailwindcss để styling cho ứng dụng. Các bước setup tích hợp Tailwind vào ứng dụng làm theo đúng [guide](https://tailwindcss.com/docs/guides/nextjs#creating-your-project) của họ. 

Tuy nhiên, không hiểu vì sao, trong quá trình phát triển, app của mình lại mất rất nhiều thời gian để reload trong môi trường local development. Mình không đo lường, nhưng ước chừng toàn mất khoảng 5-10s để reload sau khi mình chỉnh sửa 1 vài dòng JS/CSS. Để cho đỡ chờ lâu, mình toàn F5 cả trang lại cho nhanh.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629640953981/ARCeaPD-4.png)

Hôm nay thì đang rảnh, với ứng dụng đang bắt đầu lớn dần lên, mình không thể làm ngơ trước cái issue này. Sau một hồi google thì nhận ra vấn đề là do ở Tailwind, chứ không phải ở Nextjs. Mặc định, mỗi khi reload, Nextjs sẽ gọi tới file config của Tailwind để **generate-lại-toàn-bộ** CSS. Vấn đề xảy ra ở đó, làm cho ứng dụng mất nhiều thời gian để build lại. Vấn đề này xảy ra khi mình import css của Tailwind vào bằng `@base` và sử dụng các extended config, không xảy ra khi import trực tiếp Tailwindcss.

Rất may, tại phiên bản 2.1 của Tailwind, họ đã cho ra mắt tính năng [just-in-time](https://tailwindcss.com/docs/just-in-time-mode). Tính năng này giúp giảm thiểu thời gian build lại CSS của Tailwind, nó chỉ được generate lại khi có sử thay đổi trong template của bạn. Kích hoạt bằng cách thêm option sau vào file `tailwind.config.js`: 

```
module.exports = {
    ...
    mode: 'jit',
    ...
}
```

Vấn đề đã được giải quyết. Save code xong chưa kịp chuyển sang cửa sổ browser thì ứng dụng đã được reload lại rồi!