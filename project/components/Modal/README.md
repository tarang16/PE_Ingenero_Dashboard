# Modal

Bootstrap modal, re-skinned: vertically centred, `radius-2px` dialog with no border; 10px header with a primary_gray_3 rule and a gray close icon (2vmin in a 2.8vmin square); borderless 10px footer. Custom headers (`CustomModal`) use a 5vmin `.mainHeader`.

**Consumer provides:** title, body content and footer buttons (reset/cancel left, primary right). Choose a width preset: `modal-md` 80vmin, `modal-lg` 120vmin, `modal-xl` 160vmin.

- Backdrop `rgba(0,0,0,0.5)`; nested modals add 10 to z-index from `z-modal-backdrop` (1040) to 1080.
- Draggable variant (`.react-draggable`): 1px primary_blue border, `radius-4px`, `boxShadow_card`.
