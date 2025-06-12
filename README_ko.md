[KO](./README_ko.md) | [EN](./README.md)

# CROCSS (Component-Role-Option-Condition Style System) Guide

CROCSS(Component-Role-Option-Condition Style System)은 구조 중심의 명확하고 직관적인 CSS 방법론입니다.

## 📐 네이밍 규칙

```
[com-]역할[-기능] [--상태] [ctx-*]
```

| 요소         | 설명                                             |
| ------------ | ------------------------------------------------ |
| `com-`       | 독립형 컴포넌트 (Modal, Selector 등)             |
| 역할(Role)   | 필수 구조명 (예: `modal`, `field`, `btn`)        |
| 기능(Option) | 하위 기능 단위 (예: `-icon`, `-clear`)           |
| 상태         | `--상태명` 형식 (예: `--active`, `--disabled`)   |
| 컨텍스트     | `ctx-*`, 사용되는 문맥을 나타냄 (예: `ctx-auth`) |

## 📏 구조 접두사 규칙

| 접두사    | 의미                                 | 예시                                     |
| --------- | ------------------------------------ | ---------------------------------------- |
| `page-`   | 페이지 단위                          | `page-login`                             |
| `area-`   | 시각적 영역                          | `area-header`                            |
| `box-`    | 기능적 묶음                          | `box-form`                               |
| `group-`  | 동일 목적 요소 묶음                  | `group-btn`                              |
| `layout-` | **공통 레이아웃 구성 요소에만 사용** | `layout-main` (❌ 일반 구조에 사용 금지) |

구조 접두사 위계

-   `page` > `area` > `box` > `group`
-   `layout` : 개별 사용

## 🧭 상태 클래스 규칙

-   `--`로 시작하며 다른 클래스와 공백으로 분리
-   상태는 단독 선택자로 사용 불가능

```html
<button class="btn-item --active">Click me</button>
```

## 🌐 컨텍스트 클래스 규칙

-   `ctx-*`는 타 클래스와 **함께만** 사용 가능
-   단독 선택자 **사용 금지**

```scss
/* ✅ 허용 */
.ctx-auth.com-modal { ... }
.ctx-auth.com-modal .area-container { ... }

/* ❌ 금지 */
.ctx-class-room { ... }
```

## 🧱 선택자 Depth 규칙

-   최대 **5단계**까지만 허용

```scss
/* ✅ */
.ctx-class-room.com-modal .area-container .group-btn .btn-item {
}

/* ❌ */
.ctx-class-room.com-modal .area-container .group-btn .btn-item .icon {
}
```
