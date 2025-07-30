# 🛒 SAGE eCommerce Conversion Tracking Integration

This project implements Google Ads and Meta Pixel conversion tracking on a SAGE-hosted promotional products website that does not offer a traditional thank-you page. Instead, it leverages the `Section 31` and `Section 32` editable areas of the SAGE Cart (SendCart) page and uses iframe DOM extraction to pass dynamic order values (Cart Number, Order Total, etc.) into Google Ads and Facebook Pixel tracking.

---

## ✅ Achievements

| Feature | Status |
|---------|--------|
| Injected inline JavaScript into Section 32 | ✅
| Extracted order data from iframe (`#WE_Frame`) | ✅
| Fallback method to manually load `gtag.js` if not present | ✅
| Fired Google Ads conversion with Cart Number and Order Total | ✅
| Verified pixel firing in browser console | ✅
| Maintained user-friendly order summary on confirmation page | ✅
| Meta Pixel "Purchase" event also included | ✅

---

## 🧠 Technical Highlights

- **Iframe DOM Access:**  
  Used `document.querySelector('#WE_Frame').contentDocument` to access cart confirmation data inside the iframe.

- **Custom Data Injection (Section 31):**  
  Hidden `<div>` with `data-` attributes injected order values for clean JS parsing.

  ```html
  <div id="order-data" style="display:none;">
    <div 
      data-cart="<CartNum>" 
      data-name="<UserFullName>" 
      data-email="<UserEmail>" 
      data-total="<OrderTotal>" 
      data-balance="<OrderBalance>">
    </div>
  </div>
