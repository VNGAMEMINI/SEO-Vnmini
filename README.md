
## Hướng dẫn về Quy ước CSS

Tài liệu này mô tả các quy ước và nguyên tắc được sử dụng trong file CSS của dự án để đảm bảo tính nhất quán, dễ đọc và dễ bảo trì.

### 1. Tính Sạch (Cleanliness)

Để đảm bảo mã CSS luôn sạch sẽ và có cấu trúc rõ ràng, chúng ta tuân thủ các nguyên tắc sau:

*   **Sắp xếp code theo cấu trúc tài liệu:**
    *   Sử dụng các thẻ có tính tài liệu như `header`, `section`, `article`, `footer`,... để tạo cấu trúc tài liệu HTML rõ ràng.
    *   Đặt tên `ID` cho các thẻ tài liệu để dễ tìm kiếm và chỉnh sửa (tùy theo nhu cầu).
    *   **Ví dụ:**
        ```html
        <!--* ----- ----- ----- menu ----- ----- ----- -->
        <section id="menu-header">
          <!--* ----- ----- container ----- ----- -->
          <div class="box__container">
            <a href="#" class="link">Hello</a>
          </div>
          <!--* ----- ----- welcome ----- ----- -->
          <span class="text__welcome">Chào mừng <b class="you">bạn</b>!</span>
        </section>
        ```

*   **Tạo cấu trúc tài liệu CSS rõ ràng:**
    *   Đặt tên `ID` và `Class` rõ ràng, có ý nghĩa.
    *   Nhóm các phần liên quan lại với nhau.
    *   Sử dụng comment để phân biệt các phần khác nhau.
    *   Sử dụng quy ước comment để nhận diện được các phần quan trọng.

*   **Hạn chế sử dụng ID cho styling, ưu tiên Class và BEM:**
    *   **Hạn chế sử dụng ID vào style:** Điều này sẽ gây khó khăn cho việc tái sử dụng CSS.
    *   **Ưu tiên sử dụng Class vào style:** Điều này sẽ dễ dàng cho việc tái sử dụng.
    *   **Sử dụng BEM (Block-Element-Modifier):** Để nhóm các chức năng quan trọng, có ý nghĩa rõ ràng và có thể tái sử dụng.
    *   **Sử dụng BEM linh hoạt có ký hiệu:**
        *   **Nên sử dụng:**
            ```html
            <!--* ----- ----- welcome ----- ----- -->
            <p class="text__welcome">
              <u>Chào mừng</u> bạn đến với trang <strong class="seo">SEO</strong>
            </p>
            ```
        *   **Hạn chế sử dụng:**
            ```html
            <!--* ----- ----- welcome ----- ----- -->
            <p class="text__welcome">
              <u class="text__lo">Chào mừng</u> bạn đến với trang <strong class="text__seo">SEO</strong>
            </p>
            ```
            *Lý do hạn chế: `text__lo` và `text__seo` có thể quá cụ thể và khó tái sử dụng cho các trường hợp khác ngoài `text__welcome`.*

### 2. Tính Bảo Trì (Maintainability)

Để đảm bảo mã CSS dễ dàng bảo trì và mở rộng, chúng ta áp dụng các quy ước sau:

*   **Quy ước Comment Element theo thứ tự:**
    *   **Element tài liệu (Document Elements):** `/** ----- ----- -----` 
        HOẶC `/** (((`
    *   **Element Class BEM cấp 1 (Block):** `/** ----- -----` 
        HOẶC `/** ((`
    *   **Element Class BEM cấp 2 (Element):** `/** -----` 
        HOẶC `/** (`
    *   **Element Class đơn (Single Class):** `/** ---`

*   **Quy ước Comment quan trọng:** `/** =====`
    *   Để nhận diện được các phần quan trọng.
    *   Để phân biệt được các phần khác nhau.
    *   Để phân biệt được các phần có sự thay đổi.
    *   Để dễ dàng tìm kiếm và chỉnh sửa.

*   **Sử dụng biến CSS (`:root`) để quản lý giá trị:**
    *   Sử dụng `:root` làm nơi tập trung định nghĩa các biến CSS toàn cục.
    *   Sử dụng tên `ID` của một tài liệu (nếu có) để nhóm các biến liên quan đến phần đó.
    *   **Ví dụ:**
        ```css
        :root {
          /* Biến toàn cục */
          --color-primary: #38bdf8;
        }

        #name { /* Ví dụ cho một phần cụ thể */
          /* Sử dụng var() để tái sử dụng giá trị */
          /* Tên biến quy ước theo tên nhóm: */
          --name-variable: value; /* ←- giá trị gốc */
          --name-variable-: value; /* ←- giá trị biến đổi (nếu có) */
          --variable: value; /* ←- giá trị chung (nếu có) */
          --variable-: value; /* ←- giá trị chung biến đổi (nếu có) */
        }
        ```
        *Lưu ý: Trong ví dụ trên, `#name` là một placeholder. Trong thực tế, bạn sẽ định nghĩa các biến cụ thể trong `:root` hoặc trong các selector cụ thể nếu chúng chỉ áp dụng cho một phạm vi nhất định.*
