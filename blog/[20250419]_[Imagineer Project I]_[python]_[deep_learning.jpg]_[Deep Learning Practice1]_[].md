# Deep Learning Practice

MNIST 숫자 이미지 분류를 딥러닝으로 해보는 기본적인 예제

<br/>

- 숫자 손글씨 사진을 보고 어떤 숫자인지 맞추는 딥러닝 모델을 만들고  
- 학습시키고  
- 테스트하고  
- 결과를 그림으로 보여준다.

<br/>

<p>
  <iframe
    src="https://nbviewer.org/gist/ShawnKim2/d2dee5c7580dacd29c79b55fbe870a24"
    width= "800px"
    height= "1000"
    frameborder="0"
    scrolling="yes">
  </iframe>
</p>

<br/>

- 안 보일 경우:

<br/>

<p>
  <!DOCTYPE html>
  <html>
  <head><meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <title>딥러닝_1주차_1</title><script src="https://cdnjs.cloudflare.com/ajax/libs/require.js/2.1.10/require.min.js"></script>




  <style type="text/css">
      pre { line-height: 125%; }
  td.linenos .normal { color: inherit; background-color: transparent; padding-left: 5px; padding-right: 5px; }
  span.linenos { color: inherit; background-color: transparent; padding-left: 5px; padding-right: 5px; }
  td.linenos .special { color: #000000; background-color: #ffffc0; padding-left: 5px; padding-right: 5px; }
  span.linenos.special { color: #000000; background-color: #ffffc0; padding-left: 5px; padding-right: 5px; }
  .highlight .hll { background-color: var(--jp-cell-editor-active-background) }
  .highlight { background: var(--jp-cell-editor-background); color: var(--jp-mirror-editor-variable-color) }
  .highlight .c { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment */
  .highlight .err { color: var(--jp-mirror-editor-error-color) } /* Error */
  .highlight .k { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword */
  .highlight .o { color: var(--jp-mirror-editor-operator-color); font-weight: bold } /* Operator */
  .highlight .p { color: var(--jp-mirror-editor-punctuation-color) } /* Punctuation */
  .highlight .ch { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.Hashbang */
  .highlight .cm { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.Multiline */
  .highlight .cp { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.Preproc */
  .highlight .cpf { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.PreprocFile */
  .highlight .c1 { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.Single */
  .highlight .cs { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.Special */
  .highlight .kc { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Constant */
  .highlight .kd { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Declaration */
  .highlight .kn { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Namespace */
  .highlight .kp { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Pseudo */
  .highlight .kr { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Reserved */
  .highlight .kt { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Type */
  .highlight .m { color: var(--jp-mirror-editor-number-color) } /* Literal.Number */
  .highlight .s { color: var(--jp-mirror-editor-string-color) } /* Literal.String */
  .highlight .ow { color: var(--jp-mirror-editor-operator-color); font-weight: bold } /* Operator.Word */
  .highlight .w { color: var(--jp-mirror-editor-variable-color) } /* Text.Whitespace */
  .highlight .mb { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Bin */
  .highlight .mf { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Float */
  .highlight .mh { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Hex */
  .highlight .mi { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Integer */
  .highlight .mo { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Oct */
  .highlight .sa { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Affix */
  .highlight .sb { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Backtick */
  .highlight .sc { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Char */
  .highlight .dl { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Delimiter */
  .highlight .sd { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Doc */
  .highlight .s2 { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Double */
  .highlight .se { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Escape */
  .highlight .sh { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Heredoc */
  .highlight .si { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Interpol */
  .highlight .sx { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Other */
  .highlight .sr { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Regex */
  .highlight .s1 { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Single */
  .highlight .ss { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Symbol */
  .highlight .il { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Integer.Long */
    </style>



  <style type="text/css">
  /*-----------------------------------------------------------------------------
  | Copyright (c) Jupyter Development Team.
  | Distributed under the terms of the Modified BSD License.
  |----------------------------------------------------------------------------*/

  /*
  * Mozilla scrollbar styling
  */

  /* use standard opaque scrollbars for most nodes */
  [data-jp-theme-scrollbars='true'] {
    scrollbar-color: rgb(var(--jp-scrollbar-thumb-color))
      var(--jp-scrollbar-background-color);
  }

  /* for code nodes, use a transparent style of scrollbar. These selectors
  * will match lower in the tree, and so will override the above */
  [data-jp-theme-scrollbars='true'] .CodeMirror-hscrollbar,
  [data-jp-theme-scrollbars='true'] .CodeMirror-vscrollbar {
    scrollbar-color: rgba(var(--jp-scrollbar-thumb-color), 0.5) transparent;
  }

  /* tiny scrollbar */

  .jp-scrollbar-tiny {
    scrollbar-color: rgba(var(--jp-scrollbar-thumb-color), 0.5) transparent;
    scrollbar-width: thin;
  }

  /*
  * Webkit scrollbar styling
  */

  /* use standard opaque scrollbars for most nodes */

  [data-jp-theme-scrollbars='true'] ::-webkit-scrollbar,
  [data-jp-theme-scrollbars='true'] ::-webkit-scrollbar-corner {
    background: var(--jp-scrollbar-background-color);
  }

  [data-jp-theme-scrollbars='true'] ::-webkit-scrollbar-thumb {
    background: rgb(var(--jp-scrollbar-thumb-color));
    border: var(--jp-scrollbar-thumb-margin) solid transparent;
    background-clip: content-box;
    border-radius: var(--jp-scrollbar-thumb-radius);
  }

  [data-jp-theme-scrollbars='true'] ::-webkit-scrollbar-track:horizontal {
    border-left: var(--jp-scrollbar-endpad) solid
      var(--jp-scrollbar-background-color);
    border-right: var(--jp-scrollbar-endpad) solid
      var(--jp-scrollbar-background-color);
  }

  [data-jp-theme-scrollbars='true'] ::-webkit-scrollbar-track:vertical {
    border-top: var(--jp-scrollbar-endpad) solid
      var(--jp-scrollbar-background-color);
    border-bottom: var(--jp-scrollbar-endpad) solid
      var(--jp-scrollbar-background-color);
  }

  /* for code nodes, use a transparent style of scrollbar */

  [data-jp-theme-scrollbars='true'] .CodeMirror-hscrollbar::-webkit-scrollbar,
  [data-jp-theme-scrollbars='true'] .CodeMirror-vscrollbar::-webkit-scrollbar,
  [data-jp-theme-scrollbars='true']
    .CodeMirror-hscrollbar::-webkit-scrollbar-corner,
  [data-jp-theme-scrollbars='true']
    .CodeMirror-vscrollbar::-webkit-scrollbar-corner {
    background-color: transparent;
  }

  [data-jp-theme-scrollbars='true']
    .CodeMirror-hscrollbar::-webkit-scrollbar-thumb,
  [data-jp-theme-scrollbars='true']
    .CodeMirror-vscrollbar::-webkit-scrollbar-thumb {
    background: rgba(var(--jp-scrollbar-thumb-color), 0.5);
    border: var(--jp-scrollbar-thumb-margin) solid transparent;
    background-clip: content-box;
    border-radius: var(--jp-scrollbar-thumb-radius);
  }

  [data-jp-theme-scrollbars='true']
    .CodeMirror-hscrollbar::-webkit-scrollbar-track:horizontal {
    border-left: var(--jp-scrollbar-endpad) solid transparent;
    border-right: var(--jp-scrollbar-endpad) solid transparent;
  }

  [data-jp-theme-scrollbars='true']
    .CodeMirror-vscrollbar::-webkit-scrollbar-track:vertical {
    border-top: var(--jp-scrollbar-endpad) solid transparent;
    border-bottom: var(--jp-scrollbar-endpad) solid transparent;
  }

  /* tiny scrollbar */

  .jp-scrollbar-tiny::-webkit-scrollbar,
  .jp-scrollbar-tiny::-webkit-scrollbar-corner {
    background-color: transparent;
    height: 4px;
    width: 4px;
  }

  .jp-scrollbar-tiny::-webkit-scrollbar-thumb {
    background: rgba(var(--jp-scrollbar-thumb-color), 0.5);
  }

  .jp-scrollbar-tiny::-webkit-scrollbar-track:horizontal {
    border-left: 0px solid transparent;
    border-right: 0px solid transparent;
  }

  .jp-scrollbar-tiny::-webkit-scrollbar-track:vertical {
    border-top: 0px solid transparent;
    border-bottom: 0px solid transparent;
  }

  /*
  * Phosphor
  */

  .lm-ScrollBar[data-orientation='horizontal'] {
    min-height: 16px;
    max-height: 16px;
    min-width: 45px;
    border-top: 1px solid #a0a0a0;
  }

  .lm-ScrollBar[data-orientation='vertical'] {
    min-width: 16px;
    max-width: 16px;
    min-height: 45px;
    border-left: 1px solid #a0a0a0;
  }

  .lm-ScrollBar-button {
    background-color: #f0f0f0;
    background-position: center center;
    min-height: 15px;
    max-height: 15px;
    min-width: 15px;
    max-width: 15px;
  }

  .lm-ScrollBar-button:hover {
    background-color: #dadada;
  }

  .lm-ScrollBar-button.lm-mod-active {
    background-color: #cdcdcd;
  }

  .lm-ScrollBar-track {
    background: #f0f0f0;
  }

  .lm-ScrollBar-thumb {
    background: #cdcdcd;
  }

  .lm-ScrollBar-thumb:hover {
    background: #bababa;
  }

  .lm-ScrollBar-thumb.lm-mod-active {
    background: #a0a0a0;
  }

  .lm-ScrollBar[data-orientation='horizontal'] .lm-ScrollBar-thumb {
    height: 100%;
    min-width: 15px;
    border-left: 1px solid #a0a0a0;
    border-right: 1px solid #a0a0a0;
  }

  .lm-ScrollBar[data-orientation='vertical'] .lm-ScrollBar-thumb {
    width: 100%;
    min-height: 15px;
    border-top: 1px solid #a0a0a0;
    border-bottom: 1px solid #a0a0a0;
  }

  .lm-ScrollBar[data-orientation='horizontal']
    .lm-ScrollBar-button[data-action='decrement'] {
    background-image: var(--jp-icon-caret-left);
    background-size: 17px;
  }

  .lm-ScrollBar[data-orientation='horizontal']
    .lm-ScrollBar-button[data-action='increment'] {
    background-image: var(--jp-icon-caret-right);
    background-size: 17px;
  }

  .lm-ScrollBar[data-orientation='vertical']
    .lm-ScrollBar-button[data-action='decrement'] {
    background-image: var(--jp-icon-caret-up);
    background-size: 17px;
  }

  .lm-ScrollBar[data-orientation='vertical']
    .lm-ScrollBar-button[data-action='increment'] {
    background-image: var(--jp-icon-caret-down);
    background-size: 17px;
  }

  /*-----------------------------------------------------------------------------
  | Copyright (c) Jupyter Development Team.
  | Copyright (c) 2014-2017, PhosphorJS Contributors
  |
  | Distributed under the terms of the BSD 3-Clause License.
  |
  | The full license is in the file LICENSE, distributed with this software.
  |----------------------------------------------------------------------------*/


  /* <DEPRECATED> */ .p-Widget, /* </DEPRECATED> */
  .lm-Widget {
    box-sizing: border-box;
    position: relative;
    overflow: hidden;
    cursor: default;
  }


  /* <DEPRECATED> */ .p-Widget.p-mod-hidden, /* </DEPRECATED> */
  .lm-Widget.lm-mod-hidden {
    display: none !important;
  }

  /*-----------------------------------------------------------------------------
  | Copyright (c) Jupyter Development Team.
  | Copyright (c) 2014-2017, PhosphorJS Contributors
  |
  | Distributed under the terms of the BSD 3-Clause License.
  |
  | The full license is in the file LICENSE, distributed with this software.
  |----------------------------------------------------------------------------*/


  /* <DEPRECATED> */ .p-CommandPalette, /* </DEPRECATED> */
  .lm-CommandPalette {
    display: flex;
    flex-direction: column;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
  }


  /* <DEPRECATED> */ .p-CommandPalette-search, /* </DEPRECATED> */
  .lm-CommandPalette-search {
    flex: 0 0 auto;
  }


  /* <DEPRECATED> */ .p-CommandPalette-content, /* </DEPRECATED> */
  .lm-CommandPalette-content {
    flex: 1 1 auto;
    margin: 0;
    padding: 0;
    min-height: 0;
    overflow: auto;
    list-style-type: none;
  }


  /* <DEPRECATED> */ .p-CommandPalette-header, /* </DEPRECATED> */
  .lm-CommandPalette-header {
    overflow: hidden;
    white-space: nowrap;
    text-overflow: ellipsis;
  }


  /* <DEPRECATED> */ .p-CommandPalette-item, /* </DEPRECATED> */
  .lm-CommandPalette-item {
    display: flex;
    flex-direction: row;
  }


  /* <DEPRECATED> */ .p-CommandPalette-itemIcon, /* </DEPRECATED> */
  .lm-CommandPalette-itemIcon {
    flex: 0 0 auto;
  }


  /* <DEPRECATED> */ .p-CommandPalette-itemContent, /* </DEPRECATED> */
  .lm-CommandPalette-itemContent {
    flex: 1 1 auto;
    overflow: hidden;
  }


  /* <DEPRECATED> */ .p-CommandPalette-itemShortcut, /* </DEPRECATED> */
  .lm-CommandPalette-itemShortcut {
    flex: 0 0 auto;
  }


  /* <DEPRECATED> */ .p-CommandPalette-itemLabel, /* </DEPRECATED> */
  .lm-CommandPalette-itemLabel {
    overflow: hidden;
    white-space: nowrap;
    text-overflow: ellipsis;
  }

  .lm-close-icon {
    border:1px solid transparent;
    background-color: transparent;
    position: absolute;
    z-index:1;
    right:3%;
    top: 0;
    bottom: 0;
    margin: auto;
    padding: 7px 0;
    display: none;
    vertical-align: middle;
    outline: 0;
    cursor: pointer;
  }
  .lm-close-icon:after {
    content: "X";
    display: block;
    width: 15px;
    height: 15px;
    text-align: center;
    color:#000;
    font-weight: normal;
    font-size: 12px;
    cursor: pointer;
  }

  /*-----------------------------------------------------------------------------
  | Copyright (c) Jupyter Development Team.
  | Copyright (c) 2014-2017, PhosphorJS Contributors
  |
  | Distributed under the terms of the BSD 3-Clause License.
  |
  | The full license is in the file LICENSE, distributed with this software.
  |----------------------------------------------------------------------------*/


  /* <DEPRECATED> */ .p-DockPanel, /* </DEPRECATED> */
  .lm-DockPanel {
    z-index: 0;
  }


  /* <DEPRECATED> */ .p-DockPanel-widget, /* </DEPRECATED> */
  .lm-DockPanel-widget {
    z-index: 0;
  }


  /* <DEPRECATED> */ .p-DockPanel-tabBar, /* </DEPRECATED> */
  .lm-DockPanel-tabBar {
    z-index: 1;
  }


  /* <DEPRECATED> */ .p-DockPanel-handle, /* </DEPRECATED> */
  .lm-DockPanel-handle {
    z-index: 2;
  }


  /* <DEPRECATED> */ .p-DockPanel-handle.p-mod-hidden, /* </DEPRECATED> */
  .lm-DockPanel-handle.lm-mod-hidden {
    display: none !important;
  }


  /* <DEPRECATED> */ .p-DockPanel-handle:after, /* </DEPRECATED> */
  .lm-DockPanel-handle:after {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    content: '';
  }


  /* <DEPRECATED> */
  .p-DockPanel-handle[data-orientation='horizontal'],
  /* </DEPRECATED> */
  .lm-DockPanel-handle[data-orientation='horizontal'] {
    cursor: ew-resize;
  }


  /* <DEPRECATED> */
  .p-DockPanel-handle[data-orientation='vertical'],
  /* </DEPRECATED> */
  .lm-DockPanel-handle[data-orientation='vertical'] {
    cursor: ns-resize;
  }


  /* <DEPRECATED> */
  .p-DockPanel-handle[data-orientation='horizontal']:after,
  /* </DEPRECATED> */
  .lm-DockPanel-handle[data-orientation='horizontal']:after {
    left: 50%;
    min-width: 8px;
    transform: translateX(-50%);
  }


  /* <DEPRECATED> */
  .p-DockPanel-handle[data-orientation='vertical']:after,
  /* </DEPRECATED> */
  .lm-DockPanel-handle[data-orientation='vertical']:after {
    top: 50%;
    min-height: 8px;
    transform: translateY(-50%);
  }


  /* <DEPRECATED> */ .p-DockPanel-overlay, /* </DEPRECATED> */
  .lm-DockPanel-overlay {
    z-index: 3;
    box-sizing: border-box;
    pointer-events: none;
  }


  /* <DEPRECATED> */ .p-DockPanel-overlay.p-mod-hidden, /* </DEPRECATED> */
  .lm-DockPanel-overlay.lm-mod-hidden {
    display: none !important;
  }

  /*-----------------------------------------------------------------------------
  | Copyright (c) Jupyter Development Team.
  | Copyright (c) 2014-2017, PhosphorJS Contributors
  |
  | Distributed under the terms of the BSD 3-Clause License.
  |
  | The full license is in the file LICENSE, distributed with this software.
  |----------------------------------------------------------------------------*/


  /* <DEPRECATED> */ .p-Menu, /* </DEPRECATED> */
  .lm-Menu {
    z-index: 10000;
    position: absolute;
    white-space: nowrap;
    overflow-x: hidden;
    overflow-y: auto;
    outline: none;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
  }


  /* <DEPRECATED> */ .p-Menu-content, /* </DEPRECATED> */
  .lm-Menu-content {
    margin: 0;
    padding: 0;
    display: table;
    list-style-type: none;
  }


  /* <DEPRECATED> */ .p-Menu-item, /* </DEPRECATED> */
  .lm-Menu-item {
    display: table-row;
  }


  /* <DEPRECATED> */
  .p-Menu-item.p-mod-hidden,
  .p-Menu-item.p-mod-collapsed,
  /* </DEPRECATED> */
  .lm-Menu-item.lm-mod-hidden,
  .lm-Menu-item.lm-mod-collapsed {
    display: none !important;
  }


  /* <DEPRECATED> */
  .p-Menu-itemIcon,
  .p-Menu-itemSubmenuIcon,
  /* </DEPRECATED> */
  .lm-Menu-itemIcon,
  .lm-Menu-itemSubmenuIcon {
    display: table-cell;
    text-align: center;
  }


  /* <DEPRECATED> */ .p-Menu-itemLabel, /* </DEPRECATED> */
  .lm-Menu-itemLabel {
    display: table-cell;
    text-align: left;
  }


  /* <DEPRECATED> */ .p-Menu-itemShortcut, /* </DEPRECATED> */
  .lm-Menu-itemShortcut {
    display: table-cell;
    text-align: right;
  }

  /*-----------------------------------------------------------------------------
  | Copyright (c) Jupyter Development Team.
  | Copyright (c) 2014-2017, PhosphorJS Contributors
  |
  | Distributed under the terms of the BSD 3-Clause License.
  |
  | The full license is in the file LICENSE, distributed with this software.
  |----------------------------------------------------------------------------*/


  /* <DEPRECATED> */ .p-MenuBar, /* </DEPRECATED> */
  .lm-MenuBar {
    outline: none;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
  }


  /* <DEPRECATED> */ .p-MenuBar-content, /* </DEPRECATED> */
  .lm-MenuBar-content {
    margin: 0;
    padding: 0;
    display: flex;
    flex-direction: row;
    list-style-type: none;
  }


  /* <DEPRECATED> */ .p--MenuBar-item, /* </DEPRECATED> */
  .lm-MenuBar-item {
    box-sizing: border-box;
  }


  /* <DEPRECATED> */
  .p-MenuBar-itemIcon,
  .p-MenuBar-itemLabel,
  /* </DEPRECATED> */
  .lm-MenuBar-itemIcon,
  .lm-MenuBar-itemLabel {
    display: inline-block;
  }

  /*-----------------------------------------------------------------------------
  | Copyright (c) Jupyter Development Team.
  | Copyright (c) 2014-2017, PhosphorJS Contributors
  |
  | Distributed under the terms of the BSD 3-Clause License.
  |
  | The full license is in the file LICENSE, distributed with this software.
  |----------------------------------------------------------------------------*/


  /* <DEPRECATED> */ .p-ScrollBar, /* </DEPRECATED> */
  .lm-ScrollBar {
    display: flex;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
  }


  /* <DEPRECATED> */
  .p-ScrollBar[data-orientation='horizontal'],
  /* </DEPRECATED> */
  .lm-ScrollBar[data-orientation='horizontal'] {
    flex-direction: row;
  }


  /* <DEPRECATED> */
  .p-ScrollBar[data-orientation='vertical'],
  /* </DEPRECATED> */
  .lm-ScrollBar[data-orientation='vertical'] {
    flex-direction: column;
  }


  /* <DEPRECATED> */ .p-ScrollBar-button, /* </DEPRECATED> */
  .lm-ScrollBar-button {
    box-sizing: border-box;
    flex: 0 0 auto;
  }


  /* <DEPRECATED> */ .p-ScrollBar-track, /* </DEPRECATED> */
  .lm-ScrollBar-track {
    box-sizing: border-box;
    position: relative;
    overflow: hidden;
    flex: 1 1 auto;
  }


  /* <DEPRECATED> */ .p-ScrollBar-thumb, /* </DEPRECATED> */
  .lm-ScrollBar-thumb {
    box-sizing: border-box;
    position: absolute;
  }

  /*-----------------------------------------------------------------------------
  | Copyright (c) Jupyter Development Team.
  | Copyright (c) 2014-2017, PhosphorJS Contributors
  |
  | Distributed under the terms of the BSD 3-Clause License.
  |
  | The full license is in the file LICENSE, distributed with this software.
  |----------------------------------------------------------------------------*/


  /* <DEPRECATED> */ .p-SplitPanel-child, /* </DEPRECATED> */
  .lm-SplitPanel-child {
    z-index: 0;
  }


  /* <DEPRECATED> */ .p-SplitPanel-handle, /* </DEPRECATED> */
  .lm-SplitPanel-handle {
    z-index: 1;
  }


  /* <DEPRECATED> */ .p-SplitPanel-handle.p-mod-hidden, /* </DEPRECATED> */
  .lm-SplitPanel-handle.lm-mod-hidden {
    display: none !important;
  }


  /* <DEPRECATED> */ .p-SplitPanel-handle:after, /* </DEPRECATED> */
  .lm-SplitPanel-handle:after {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    content: '';
  }


  /* <DEPRECATED> */
  .p-SplitPanel[data-orientation='horizontal'] > .p-SplitPanel-handle,
  /* </DEPRECATED> */
  .lm-SplitPanel[data-orientation='horizontal'] > .lm-SplitPanel-handle {
    cursor: ew-resize;
  }


  /* <DEPRECATED> */
  .p-SplitPanel[data-orientation='vertical'] > .p-SplitPanel-handle,
  /* </DEPRECATED> */
  .lm-SplitPanel[data-orientation='vertical'] > .lm-SplitPanel-handle {
    cursor: ns-resize;
  }


  /* <DEPRECATED> */
  .p-SplitPanel[data-orientation='horizontal'] > .p-SplitPanel-handle:after,
  /* </DEPRECATED> */
  .lm-SplitPanel[data-orientation='horizontal'] > .lm-SplitPanel-handle:after {
    left: 50%;
    min-width: 8px;
    transform: translateX(-50%);
  }


  /* <DEPRECATED> */
  .p-SplitPanel[data-orientation='vertical'] > .p-SplitPanel-handle:after,
  /* </DEPRECATED> */
  .lm-SplitPanel[data-orientation='vertical'] > .lm-SplitPanel-handle:after {
    top: 50%;
    min-height: 8px;
    transform: translateY(-50%);
  }

  /*-----------------------------------------------------------------------------
  | Copyright (c) Jupyter Development Team.
  | Copyright (c) 2014-2017, PhosphorJS Contributors
  |
  | Distributed under the terms of the BSD 3-Clause License.
  |
  | The full license is in the file LICENSE, distributed with this software.
  |----------------------------------------------------------------------------*/


  /* <DEPRECATED> */ .p-TabBar, /* </DEPRECATED> */
  .lm-TabBar {
    display: flex;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
  }


  /* <DEPRECATED> */ .p-TabBar[data-orientation='horizontal'], /* </DEPRECATED> */
  .lm-TabBar[data-orientation='horizontal'] {
    flex-direction: row;
  }


  /* <DEPRECATED> */ .p-TabBar[data-orientation='vertical'], /* </DEPRECATED> */
  .lm-TabBar[data-orientation='vertical'] {
    flex-direction: column;
  }


  /* <DEPRECATED> */ .p-TabBar-content, /* </DEPRECATED> */
  .lm-TabBar-content {
    margin: 0;
    padding: 0;
    display: flex;
    flex: 1 1 auto;
    list-style-type: none;
  }


  /* <DEPRECATED> */
  .p-TabBar[data-orientation='horizontal'] > .p-TabBar-content,
  /* </DEPRECATED> */
  .lm-TabBar[data-orientation='horizontal'] > .lm-TabBar-content {
    flex-direction: row;
  }


  /* <DEPRECATED> */
  .p-TabBar[data-orientation='vertical'] > .p-TabBar-content,
  /* </DEPRECATED> */
  .lm-TabBar[data-orientation='vertical'] > .lm-TabBar-content {
    flex-direction: column;
  }


  /* <DEPRECATED> */ .p-TabBar-tab, /* </DEPRECATED> */
  .lm-TabBar-tab {
    display: flex;
    flex-direction: row;
    box-sizing: border-box;
    overflow: hidden;
  }


  /* <DEPRECATED> */
  .p-TabBar-tabIcon,
  .p-TabBar-tabCloseIcon,
  /* </DEPRECATED> */
  .lm-TabBar-tabIcon,
  .lm-TabBar-tabCloseIcon {
    flex: 0 0 auto;
  }


  /* <DEPRECATED> */ .p-TabBar-tabLabel, /* </DEPRECATED> */
  .lm-TabBar-tabLabel {
    flex: 1 1 auto;
    overflow: hidden;
    white-space: nowrap;
  }


  .lm-TabBar-tabInput {
    user-select: all;
    width: 100%;
    box-sizing : border-box;
  }


  /* <DEPRECATED> */ .p-TabBar-tab.p-mod-hidden, /* </DEPRECATED> */
  .lm-TabBar-tab.lm-mod-hidden {
    display: none !important;
  }


  /* <DEPRECATED> */ .p-TabBar.p-mod-dragging .p-TabBar-tab, /* </DEPRECATED> */
  .lm-TabBar.lm-mod-dragging .lm-TabBar-tab {
    position: relative;
  }


  /* <DEPRECATED> */
  .p-TabBar.p-mod-dragging[data-orientation='horizontal'] .p-TabBar-tab,
  /* </DEPRECATED> */
  .lm-TabBar.lm-mod-dragging[data-orientation='horizontal'] .lm-TabBar-tab {
    left: 0;
    transition: left 150ms ease;
  }


  /* <DEPRECATED> */
  .p-TabBar.p-mod-dragging[data-orientation='vertical'] .p-TabBar-tab,
  /* </DEPRECATED> */
  .lm-TabBar.lm-mod-dragging[data-orientation='vertical'] .lm-TabBar-tab {
    top: 0;
    transition: top 150ms ease;
  }


  /* <DEPRECATED> */
  .p-TabBar.p-mod-dragging .p-TabBar-tab.p-mod-dragging,
  /* </DEPRECATED> */
  .lm-TabBar.lm-mod-dragging .lm-TabBar-tab.lm-mod-dragging {
    transition: none;
  }

  /*-----------------------------------------------------------------------------
  | Copyright (c) Jupyter Development Team.
  | Copyright (c) 2014-2017, PhosphorJS Contributors
  |
  | Distributed under the terms of the BSD 3-Clause License.
  |
  | The full license is in the file LICENSE, distributed with this software.
  |----------------------------------------------------------------------------*/


  /* <DEPRECATED> */ .p-TabPanel-tabBar, /* </DEPRECATED> */
  .lm-TabPanel-tabBar {
    z-index: 1;
  }


  /* <DEPRECATED> */ .p-TabPanel-stackedPanel, /* </DEPRECATED> */
  .lm-TabPanel-stackedPanel {
    z-index: 0;
  }

  /*-----------------------------------------------------------------------------
  | Copyright (c) Jupyter Development Team.
  | Copyright (c) 2014-2017, PhosphorJS Contributors
  |
  | Distributed under the terms of the BSD 3-Clause License.
  |
  | The full license is in the file LICENSE, distributed with this software.
  |----------------------------------------------------------------------------*/

  @charset "UTF-8";
  html{
    -webkit-box-sizing:border-box;
            box-sizing:border-box; }

  *,
  *::before,
  *::after{
    -webkit-box-sizing:inherit;
            box-sizing:inherit; }

  body{
    font-size:14px;
    font-weight:400;
    letter-spacing:0;
    line-height:1.28581;
    text-transform:none;
    color:#182026;
    font-family:-apple-system, "BlinkMacSystemFont", "Segoe UI", "Roboto", "Oxygen", "Ubuntu", "Cantarell", "Open Sans", "Helvetica Neue", "Icons16", sans-serif; }

  p{
    margin-bottom:10px;
    margin-top:0; }

  small{
    font-size:12px; }

  strong{
    font-weight:600; }

  ::-moz-selection{
    background:rgba(125, 188, 255, 0.6); }

  ::selection{
    background:rgba(125, 188, 255, 0.6); }
  .bp3-heading{
    color:#182026;
    font-weight:600;
    margin:0 0 10px;
    padding:0; }
    .bp3-dark .bp3-heading{
      color:#f5f8fa; }

  h1.bp3-heading, .bp3-running-text h1{
    font-size:36px;
    line-height:40px; }

  h2.bp3-heading, .bp3-running-text h2{
    font-size:28px;
    line-height:32px; }

  h3.bp3-heading, .bp3-running-text h3{
    font-size:22px;
    line-height:25px; }

  h4.bp3-heading, .bp3-running-text h4{
    font-size:18px;
    line-height:21px; }

  h5.bp3-heading, .bp3-running-text h5{
    font-size:16px;
    line-height:19px; }

  h6.bp3-heading, .bp3-running-text h6{
    font-size:14px;
    line-height:16px; }
  .bp3-ui-text{
    font-size:14px;
    font-weight:400;
    letter-spacing:0;
    line-height:1.28581;
    text-transform:none; }

  .bp3-monospace-text{
    font-family:monospace;
    text-transform:none; }

  .bp3-text-muted{
    color:#5c7080; }
    .bp3-dark .bp3-text-muted{
      color:#a7b6c2; }

  .bp3-text-disabled{
    color:rgba(92, 112, 128, 0.6); }
    .bp3-dark .bp3-text-disabled{
      color:rgba(167, 182, 194, 0.6); }

  .bp3-text-overflow-ellipsis{
    overflow:hidden;
    text-overflow:ellipsis;
    white-space:nowrap;
    word-wrap:normal; }
  .bp3-running-text{
    font-size:14px;
    line-height:1.5; }
    .bp3-running-text h1{
      color:#182026;
      font-weight:600;
      margin-bottom:20px;
      margin-top:40px; }
      .bp3-dark .bp3-running-text h1{
        color:#f5f8fa; }
    .bp3-running-text h2{
      color:#182026;
      font-weight:600;
      margin-bottom:20px;
      margin-top:40px; }
      .bp3-dark .bp3-running-text h2{
        color:#f5f8fa; }
    .bp3-running-text h3{
      color:#182026;
      font-weight:600;
      margin-bottom:20px;
      margin-top:40px; }
      .bp3-dark .bp3-running-text h3{
        color:#f5f8fa; }
    .bp3-running-text h4{
      color:#182026;
      font-weight:600;
      margin-bottom:20px;
      margin-top:40px; }
      .bp3-dark .bp3-running-text h4{
        color:#f5f8fa; }
    .bp3-running-text h5{
      color:#182026;
      font-weight:600;
      margin-bottom:20px;
      margin-top:40px; }
      .bp3-dark .bp3-running-text h5{
        color:#f5f8fa; }
    .bp3-running-text h6{
      color:#182026;
      font-weight:600;
      margin-bottom:20px;
      margin-top:40px; }
      .bp3-dark .bp3-running-text h6{
        color:#f5f8fa; }
    .bp3-running-text hr{
      border:none;
      border-bottom:1px solid rgba(16, 22, 26, 0.15);
      margin:20px 0; }
      .bp3-dark .bp3-running-text hr{
        border-color:rgba(255, 255, 255, 0.15); }
    .bp3-running-text p{
      margin:0 0 10px;
      padding:0; }

  .bp3-text-large{
    font-size:16px; }

  .bp3-text-small{
    font-size:12px; }
  a{
    color:#106ba3;
    text-decoration:none; }
    a:hover{
      color:#106ba3;
      cursor:pointer;
      text-decoration:underline; }
    a .bp3-icon, a .bp3-icon-standard, a .bp3-icon-large{
      color:inherit; }
    a code,
    .bp3-dark a code{
      color:inherit; }
    .bp3-dark a,
    .bp3-dark a:hover{
      color:#48aff0; }
      .bp3-dark a .bp3-icon, .bp3-dark a .bp3-icon-standard, .bp3-dark a .bp3-icon-large,
      .bp3-dark a:hover .bp3-icon,
      .bp3-dark a:hover .bp3-icon-standard,
      .bp3-dark a:hover .bp3-icon-large{
        color:inherit; }
  .bp3-running-text code, .bp3-code{
    font-family:monospace;
    text-transform:none;
    background:rgba(255, 255, 255, 0.7);
    border-radius:3px;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2);
    color:#5c7080;
    font-size:smaller;
    padding:2px 5px; }
    .bp3-dark .bp3-running-text code, .bp3-running-text .bp3-dark code, .bp3-dark .bp3-code{
      background:rgba(16, 22, 26, 0.3);
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4);
      color:#a7b6c2; }
    .bp3-running-text a > code, a > .bp3-code{
      color:#137cbd; }
      .bp3-dark .bp3-running-text a > code, .bp3-running-text .bp3-dark a > code, .bp3-dark a > .bp3-code{
        color:inherit; }

  .bp3-running-text pre, .bp3-code-block{
    font-family:monospace;
    text-transform:none;
    background:rgba(255, 255, 255, 0.7);
    border-radius:3px;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.15);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.15);
    color:#182026;
    display:block;
    font-size:13px;
    line-height:1.4;
    margin:10px 0;
    padding:13px 15px 12px;
    word-break:break-all;
    word-wrap:break-word; }
    .bp3-dark .bp3-running-text pre, .bp3-running-text .bp3-dark pre, .bp3-dark .bp3-code-block{
      background:rgba(16, 22, 26, 0.3);
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4);
      color:#f5f8fa; }
    .bp3-running-text pre > code, .bp3-code-block > code{
      background:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:inherit;
      font-size:inherit;
      padding:0; }

  .bp3-running-text kbd, .bp3-key{
    -webkit-box-align:center;
        -ms-flex-align:center;
            align-items:center;
    background:#ffffff;
    border-radius:3px;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.2);
    color:#5c7080;
    display:-webkit-inline-box;
    display:-ms-inline-flexbox;
    display:inline-flex;
    font-family:inherit;
    font-size:12px;
    height:24px;
    -webkit-box-pack:center;
        -ms-flex-pack:center;
            justify-content:center;
    line-height:24px;
    min-width:24px;
    padding:3px 6px;
    vertical-align:middle; }
    .bp3-running-text kbd .bp3-icon, .bp3-key .bp3-icon, .bp3-running-text kbd .bp3-icon-standard, .bp3-key .bp3-icon-standard, .bp3-running-text kbd .bp3-icon-large, .bp3-key .bp3-icon-large{
      margin-right:5px; }
    .bp3-dark .bp3-running-text kbd, .bp3-running-text .bp3-dark kbd, .bp3-dark .bp3-key{
      background:#394b59;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4);
      color:#a7b6c2; }
  .bp3-running-text blockquote, .bp3-blockquote{
    border-left:solid 4px rgba(167, 182, 194, 0.5);
    margin:0 0 10px;
    padding:0 20px; }
    .bp3-dark .bp3-running-text blockquote, .bp3-running-text .bp3-dark blockquote, .bp3-dark .bp3-blockquote{
      border-color:rgba(115, 134, 148, 0.5); }
  .bp3-running-text ul,
  .bp3-running-text ol, .bp3-list{
    margin:10px 0;
    padding-left:30px; }
    .bp3-running-text ul li:not(:last-child), .bp3-running-text ol li:not(:last-child), .bp3-list li:not(:last-child){
      margin-bottom:5px; }
    .bp3-running-text ul ol, .bp3-running-text ol ol, .bp3-list ol,
    .bp3-running-text ul ul,
    .bp3-running-text ol ul,
    .bp3-list ul{
      margin-top:5px; }

  .bp3-list-unstyled{
    list-style:none;
    margin:0;
    padding:0; }
    .bp3-list-unstyled li{
      padding:0; }
  .bp3-rtl{
    text-align:right; }

  .bp3-dark{
    color:#f5f8fa; }

  :focus{
    outline:rgba(19, 124, 189, 0.6) auto 2px;
    outline-offset:2px;
    -moz-outline-radius:6px; }

  .bp3-focus-disabled :focus{
    outline:none !important; }
    .bp3-focus-disabled :focus ~ .bp3-control-indicator{
      outline:none !important; }

  .bp3-alert{
    max-width:400px;
    padding:20px; }

  .bp3-alert-body{
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex; }
    .bp3-alert-body .bp3-icon{
      font-size:40px;
      margin-right:20px;
      margin-top:0; }

  .bp3-alert-contents{
    word-break:break-word; }

  .bp3-alert-footer{
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    -webkit-box-orient:horizontal;
    -webkit-box-direction:reverse;
        -ms-flex-direction:row-reverse;
            flex-direction:row-reverse;
    margin-top:10px; }
    .bp3-alert-footer .bp3-button{
      margin-left:10px; }
  .bp3-breadcrumbs{
    -webkit-box-align:center;
        -ms-flex-align:center;
            align-items:center;
    cursor:default;
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    -ms-flex-wrap:wrap;
        flex-wrap:wrap;
    height:30px;
    list-style:none;
    margin:0;
    padding:0; }
    .bp3-breadcrumbs > li{
      -webkit-box-align:center;
          -ms-flex-align:center;
              align-items:center;
      display:-webkit-box;
      display:-ms-flexbox;
      display:flex; }
      .bp3-breadcrumbs > li::after{
        background:url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 16 16'%3e%3cpath fill-rule='evenodd' clip-rule='evenodd' d='M10.71 7.29l-4-4a1.003 1.003 0 00-1.42 1.42L8.59 8 5.3 11.29c-.19.18-.3.43-.3.71a1.003 1.003 0 001.71.71l4-4c.18-.18.29-.43.29-.71 0-.28-.11-.53-.29-.71z' fill='%235C7080'/%3e%3c/svg%3e");
        content:"";
        display:block;
        height:16px;
        margin:0 5px;
        width:16px; }
      .bp3-breadcrumbs > li:last-of-type::after{
        display:none; }

  .bp3-breadcrumb,
  .bp3-breadcrumb-current,
  .bp3-breadcrumbs-collapsed{
    -webkit-box-align:center;
        -ms-flex-align:center;
            align-items:center;
    display:-webkit-inline-box;
    display:-ms-inline-flexbox;
    display:inline-flex;
    font-size:16px; }

  .bp3-breadcrumb,
  .bp3-breadcrumbs-collapsed{
    color:#5c7080; }

  .bp3-breadcrumb:hover{
    text-decoration:none; }

  .bp3-breadcrumb.bp3-disabled{
    color:rgba(92, 112, 128, 0.6);
    cursor:not-allowed; }

  .bp3-breadcrumb .bp3-icon{
    margin-right:5px; }

  .bp3-breadcrumb-current{
    color:inherit;
    font-weight:600; }
    .bp3-breadcrumb-current .bp3-input{
      font-size:inherit;
      font-weight:inherit;
      vertical-align:baseline; }

  .bp3-breadcrumbs-collapsed{
    background:#ced9e0;
    border:none;
    border-radius:3px;
    cursor:pointer;
    margin-right:2px;
    padding:1px 5px;
    vertical-align:text-bottom; }
    .bp3-breadcrumbs-collapsed::before{
      background:url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 16 16'%3e%3cg fill='%235C7080'%3e%3ccircle cx='2' cy='8.03' r='2'/%3e%3ccircle cx='14' cy='8.03' r='2'/%3e%3ccircle cx='8' cy='8.03' r='2'/%3e%3c/g%3e%3c/svg%3e") center no-repeat;
      content:"";
      display:block;
      height:16px;
      width:16px; }
    .bp3-breadcrumbs-collapsed:hover{
      background:#bfccd6;
      color:#182026;
      text-decoration:none; }

  .bp3-dark .bp3-breadcrumb,
  .bp3-dark .bp3-breadcrumbs-collapsed{
    color:#a7b6c2; }

  .bp3-dark .bp3-breadcrumbs > li::after{
    color:#a7b6c2; }

  .bp3-dark .bp3-breadcrumb.bp3-disabled{
    color:rgba(167, 182, 194, 0.6); }

  .bp3-dark .bp3-breadcrumb-current{
    color:#f5f8fa; }

  .bp3-dark .bp3-breadcrumbs-collapsed{
    background:rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-breadcrumbs-collapsed:hover{
      background:rgba(16, 22, 26, 0.6);
      color:#f5f8fa; }
  .bp3-button{
    display:-webkit-inline-box;
    display:-ms-inline-flexbox;
    display:inline-flex;
    -webkit-box-orient:horizontal;
    -webkit-box-direction:normal;
        -ms-flex-direction:row;
            flex-direction:row;
    -webkit-box-align:center;
        -ms-flex-align:center;
            align-items:center;
    border:none;
    border-radius:3px;
    cursor:pointer;
    font-size:14px;
    -webkit-box-pack:center;
        -ms-flex-pack:center;
            justify-content:center;
    padding:5px 10px;
    text-align:left;
    vertical-align:middle;
    min-height:30px;
    min-width:30px; }
    .bp3-button > *{
      -webkit-box-flex:0;
          -ms-flex-positive:0;
              flex-grow:0;
      -ms-flex-negative:0;
          flex-shrink:0; }
    .bp3-button > .bp3-fill{
      -webkit-box-flex:1;
          -ms-flex-positive:1;
              flex-grow:1;
      -ms-flex-negative:1;
          flex-shrink:1; }
    .bp3-button::before,
    .bp3-button > *{
      margin-right:7px; }
    .bp3-button:empty::before,
    .bp3-button > :last-child{
      margin-right:0; }
    .bp3-button:empty{
      padding:0 !important; }
    .bp3-button:disabled, .bp3-button.bp3-disabled{
      cursor:not-allowed; }
    .bp3-button.bp3-fill{
      display:-webkit-box;
      display:-ms-flexbox;
      display:flex;
      width:100%; }
    .bp3-button.bp3-align-right,
    .bp3-align-right .bp3-button{
      text-align:right; }
    .bp3-button.bp3-align-left,
    .bp3-align-left .bp3-button{
      text-align:left; }
    .bp3-button:not([class*="bp3-intent-"]){
      background-color:#f5f8fa;
      background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.8)), to(rgba(255, 255, 255, 0)));
      background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.8), rgba(255, 255, 255, 0));
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
      color:#182026; }
      .bp3-button:not([class*="bp3-intent-"]):hover{
        background-clip:padding-box;
        background-color:#ebf1f5;
        -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
                box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1); }
      .bp3-button:not([class*="bp3-intent-"]):active, .bp3-button:not([class*="bp3-intent-"]).bp3-active{
        background-color:#d8e1e8;
        background-image:none;
        -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
                box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
      .bp3-button:not([class*="bp3-intent-"]):disabled, .bp3-button:not([class*="bp3-intent-"]).bp3-disabled{
        background-color:rgba(206, 217, 224, 0.5);
        background-image:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:rgba(92, 112, 128, 0.6);
        cursor:not-allowed;
        outline:none; }
        .bp3-button:not([class*="bp3-intent-"]):disabled.bp3-active, .bp3-button:not([class*="bp3-intent-"]):disabled.bp3-active:hover, .bp3-button:not([class*="bp3-intent-"]).bp3-disabled.bp3-active, .bp3-button:not([class*="bp3-intent-"]).bp3-disabled.bp3-active:hover{
          background:rgba(206, 217, 224, 0.7); }
    .bp3-button.bp3-intent-primary{
      background-color:#137cbd;
      background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.1)), to(rgba(255, 255, 255, 0)));
      background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0));
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
      color:#ffffff; }
      .bp3-button.bp3-intent-primary:hover, .bp3-button.bp3-intent-primary:active, .bp3-button.bp3-intent-primary.bp3-active{
        color:#ffffff; }
      .bp3-button.bp3-intent-primary:hover{
        background-color:#106ba3;
        -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
                box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2); }
      .bp3-button.bp3-intent-primary:active, .bp3-button.bp3-intent-primary.bp3-active{
        background-color:#0e5a8a;
        background-image:none;
        -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
                box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
      .bp3-button.bp3-intent-primary:disabled, .bp3-button.bp3-intent-primary.bp3-disabled{
        background-color:rgba(19, 124, 189, 0.5);
        background-image:none;
        border-color:transparent;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:rgba(255, 255, 255, 0.6); }
    .bp3-button.bp3-intent-success{
      background-color:#0f9960;
      background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.1)), to(rgba(255, 255, 255, 0)));
      background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0));
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
      color:#ffffff; }
      .bp3-button.bp3-intent-success:hover, .bp3-button.bp3-intent-success:active, .bp3-button.bp3-intent-success.bp3-active{
        color:#ffffff; }
      .bp3-button.bp3-intent-success:hover{
        background-color:#0d8050;
        -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
                box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2); }
      .bp3-button.bp3-intent-success:active, .bp3-button.bp3-intent-success.bp3-active{
        background-color:#0a6640;
        background-image:none;
        -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
                box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
      .bp3-button.bp3-intent-success:disabled, .bp3-button.bp3-intent-success.bp3-disabled{
        background-color:rgba(15, 153, 96, 0.5);
        background-image:none;
        border-color:transparent;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:rgba(255, 255, 255, 0.6); }
    .bp3-button.bp3-intent-warning{
      background-color:#d9822b;
      background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.1)), to(rgba(255, 255, 255, 0)));
      background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0));
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
      color:#ffffff; }
      .bp3-button.bp3-intent-warning:hover, .bp3-button.bp3-intent-warning:active, .bp3-button.bp3-intent-warning.bp3-active{
        color:#ffffff; }
      .bp3-button.bp3-intent-warning:hover{
        background-color:#bf7326;
        -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
                box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2); }
      .bp3-button.bp3-intent-warning:active, .bp3-button.bp3-intent-warning.bp3-active{
        background-color:#a66321;
        background-image:none;
        -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
                box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
      .bp3-button.bp3-intent-warning:disabled, .bp3-button.bp3-intent-warning.bp3-disabled{
        background-color:rgba(217, 130, 43, 0.5);
        background-image:none;
        border-color:transparent;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:rgba(255, 255, 255, 0.6); }
    .bp3-button.bp3-intent-danger{
      background-color:#db3737;
      background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.1)), to(rgba(255, 255, 255, 0)));
      background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0));
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
      color:#ffffff; }
      .bp3-button.bp3-intent-danger:hover, .bp3-button.bp3-intent-danger:active, .bp3-button.bp3-intent-danger.bp3-active{
        color:#ffffff; }
      .bp3-button.bp3-intent-danger:hover{
        background-color:#c23030;
        -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
                box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2); }
      .bp3-button.bp3-intent-danger:active, .bp3-button.bp3-intent-danger.bp3-active{
        background-color:#a82a2a;
        background-image:none;
        -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
                box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
      .bp3-button.bp3-intent-danger:disabled, .bp3-button.bp3-intent-danger.bp3-disabled{
        background-color:rgba(219, 55, 55, 0.5);
        background-image:none;
        border-color:transparent;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:rgba(255, 255, 255, 0.6); }
    .bp3-button[class*="bp3-intent-"] .bp3-button-spinner .bp3-spinner-head{
      stroke:#ffffff; }
    .bp3-button.bp3-large,
    .bp3-large .bp3-button{
      min-height:40px;
      min-width:40px;
      font-size:16px;
      padding:5px 15px; }
      .bp3-button.bp3-large::before,
      .bp3-button.bp3-large > *,
      .bp3-large .bp3-button::before,
      .bp3-large .bp3-button > *{
        margin-right:10px; }
      .bp3-button.bp3-large:empty::before,
      .bp3-button.bp3-large > :last-child,
      .bp3-large .bp3-button:empty::before,
      .bp3-large .bp3-button > :last-child{
        margin-right:0; }
    .bp3-button.bp3-small,
    .bp3-small .bp3-button{
      min-height:24px;
      min-width:24px;
      padding:0 7px; }
    .bp3-button.bp3-loading{
      position:relative; }
      .bp3-button.bp3-loading[class*="bp3-icon-"]::before{
        visibility:hidden; }
      .bp3-button.bp3-loading .bp3-button-spinner{
        margin:0;
        position:absolute; }
      .bp3-button.bp3-loading > :not(.bp3-button-spinner){
        visibility:hidden; }
    .bp3-button[class*="bp3-icon-"]::before{
      font-family:"Icons16", sans-serif;
      font-size:16px;
      font-style:normal;
      font-weight:400;
      line-height:1;
      -moz-osx-font-smoothing:grayscale;
      -webkit-font-smoothing:antialiased;
      color:#5c7080; }
    .bp3-button .bp3-icon, .bp3-button .bp3-icon-standard, .bp3-button .bp3-icon-large{
      color:#5c7080; }
      .bp3-button .bp3-icon.bp3-align-right, .bp3-button .bp3-icon-standard.bp3-align-right, .bp3-button .bp3-icon-large.bp3-align-right{
        margin-left:7px; }
    .bp3-button .bp3-icon:first-child:last-child,
    .bp3-button .bp3-spinner + .bp3-icon:last-child{
      margin:0 -7px; }
    .bp3-dark .bp3-button:not([class*="bp3-intent-"]){
      background-color:#394b59;
      background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.05)), to(rgba(255, 255, 255, 0)));
      background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.05), rgba(255, 255, 255, 0));
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
      color:#f5f8fa; }
      .bp3-dark .bp3-button:not([class*="bp3-intent-"]):hover, .bp3-dark .bp3-button:not([class*="bp3-intent-"]):active, .bp3-dark .bp3-button:not([class*="bp3-intent-"]).bp3-active{
        color:#f5f8fa; }
      .bp3-dark .bp3-button:not([class*="bp3-intent-"]):hover{
        background-color:#30404d;
        -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
                box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-button:not([class*="bp3-intent-"]):active, .bp3-dark .bp3-button:not([class*="bp3-intent-"]).bp3-active{
        background-color:#202b33;
        background-image:none;
        -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2);
                box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
      .bp3-dark .bp3-button:not([class*="bp3-intent-"]):disabled, .bp3-dark .bp3-button:not([class*="bp3-intent-"]).bp3-disabled{
        background-color:rgba(57, 75, 89, 0.5);
        background-image:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:rgba(167, 182, 194, 0.6); }
        .bp3-dark .bp3-button:not([class*="bp3-intent-"]):disabled.bp3-active, .bp3-dark .bp3-button:not([class*="bp3-intent-"]).bp3-disabled.bp3-active{
          background:rgba(57, 75, 89, 0.7); }
      .bp3-dark .bp3-button:not([class*="bp3-intent-"]) .bp3-button-spinner .bp3-spinner-head{
        background:rgba(16, 22, 26, 0.5);
        stroke:#8a9ba8; }
      .bp3-dark .bp3-button:not([class*="bp3-intent-"])[class*="bp3-icon-"]::before{
        color:#a7b6c2; }
      .bp3-dark .bp3-button:not([class*="bp3-intent-"]) .bp3-icon, .bp3-dark .bp3-button:not([class*="bp3-intent-"]) .bp3-icon-standard, .bp3-dark .bp3-button:not([class*="bp3-intent-"]) .bp3-icon-large{
        color:#a7b6c2; }
    .bp3-dark .bp3-button[class*="bp3-intent-"]{
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-button[class*="bp3-intent-"]:hover{
        -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
                box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-button[class*="bp3-intent-"]:active, .bp3-dark .bp3-button[class*="bp3-intent-"].bp3-active{
        -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
                box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
      .bp3-dark .bp3-button[class*="bp3-intent-"]:disabled, .bp3-dark .bp3-button[class*="bp3-intent-"].bp3-disabled{
        background-image:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:rgba(255, 255, 255, 0.3); }
      .bp3-dark .bp3-button[class*="bp3-intent-"] .bp3-button-spinner .bp3-spinner-head{
        stroke:#8a9ba8; }
    .bp3-button:disabled::before,
    .bp3-button:disabled .bp3-icon, .bp3-button:disabled .bp3-icon-standard, .bp3-button:disabled .bp3-icon-large, .bp3-button.bp3-disabled::before,
    .bp3-button.bp3-disabled .bp3-icon, .bp3-button.bp3-disabled .bp3-icon-standard, .bp3-button.bp3-disabled .bp3-icon-large, .bp3-button[class*="bp3-intent-"]::before,
    .bp3-button[class*="bp3-intent-"] .bp3-icon, .bp3-button[class*="bp3-intent-"] .bp3-icon-standard, .bp3-button[class*="bp3-intent-"] .bp3-icon-large{
      color:inherit !important; }
    .bp3-button.bp3-minimal{
      background:none;
      -webkit-box-shadow:none;
              box-shadow:none; }
      .bp3-button.bp3-minimal:hover{
        background:rgba(167, 182, 194, 0.3);
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#182026;
        text-decoration:none; }
      .bp3-button.bp3-minimal:active, .bp3-button.bp3-minimal.bp3-active{
        background:rgba(115, 134, 148, 0.3);
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#182026; }
      .bp3-button.bp3-minimal:disabled, .bp3-button.bp3-minimal:disabled:hover, .bp3-button.bp3-minimal.bp3-disabled, .bp3-button.bp3-minimal.bp3-disabled:hover{
        background:none;
        color:rgba(92, 112, 128, 0.6);
        cursor:not-allowed; }
        .bp3-button.bp3-minimal:disabled.bp3-active, .bp3-button.bp3-minimal:disabled:hover.bp3-active, .bp3-button.bp3-minimal.bp3-disabled.bp3-active, .bp3-button.bp3-minimal.bp3-disabled:hover.bp3-active{
          background:rgba(115, 134, 148, 0.3); }
      .bp3-dark .bp3-button.bp3-minimal{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:inherit; }
        .bp3-dark .bp3-button.bp3-minimal:hover, .bp3-dark .bp3-button.bp3-minimal:active, .bp3-dark .bp3-button.bp3-minimal.bp3-active{
          background:none;
          -webkit-box-shadow:none;
                  box-shadow:none; }
        .bp3-dark .bp3-button.bp3-minimal:hover{
          background:rgba(138, 155, 168, 0.15); }
        .bp3-dark .bp3-button.bp3-minimal:active, .bp3-dark .bp3-button.bp3-minimal.bp3-active{
          background:rgba(138, 155, 168, 0.3);
          color:#f5f8fa; }
        .bp3-dark .bp3-button.bp3-minimal:disabled, .bp3-dark .bp3-button.bp3-minimal:disabled:hover, .bp3-dark .bp3-button.bp3-minimal.bp3-disabled, .bp3-dark .bp3-button.bp3-minimal.bp3-disabled:hover{
          background:none;
          color:rgba(167, 182, 194, 0.6);
          cursor:not-allowed; }
          .bp3-dark .bp3-button.bp3-minimal:disabled.bp3-active, .bp3-dark .bp3-button.bp3-minimal:disabled:hover.bp3-active, .bp3-dark .bp3-button.bp3-minimal.bp3-disabled.bp3-active, .bp3-dark .bp3-button.bp3-minimal.bp3-disabled:hover.bp3-active{
            background:rgba(138, 155, 168, 0.3); }
      .bp3-button.bp3-minimal.bp3-intent-primary{
        color:#106ba3; }
        .bp3-button.bp3-minimal.bp3-intent-primary:hover, .bp3-button.bp3-minimal.bp3-intent-primary:active, .bp3-button.bp3-minimal.bp3-intent-primary.bp3-active{
          background:none;
          -webkit-box-shadow:none;
                  box-shadow:none;
          color:#106ba3; }
        .bp3-button.bp3-minimal.bp3-intent-primary:hover{
          background:rgba(19, 124, 189, 0.15);
          color:#106ba3; }
        .bp3-button.bp3-minimal.bp3-intent-primary:active, .bp3-button.bp3-minimal.bp3-intent-primary.bp3-active{
          background:rgba(19, 124, 189, 0.3);
          color:#106ba3; }
        .bp3-button.bp3-minimal.bp3-intent-primary:disabled, .bp3-button.bp3-minimal.bp3-intent-primary.bp3-disabled{
          background:none;
          color:rgba(16, 107, 163, 0.5); }
          .bp3-button.bp3-minimal.bp3-intent-primary:disabled.bp3-active, .bp3-button.bp3-minimal.bp3-intent-primary.bp3-disabled.bp3-active{
            background:rgba(19, 124, 189, 0.3); }
        .bp3-button.bp3-minimal.bp3-intent-primary .bp3-button-spinner .bp3-spinner-head{
          stroke:#106ba3; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-primary{
          color:#48aff0; }
          .bp3-dark .bp3-button.bp3-minimal.bp3-intent-primary:hover{
            background:rgba(19, 124, 189, 0.2);
            color:#48aff0; }
          .bp3-dark .bp3-button.bp3-minimal.bp3-intent-primary:active, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-primary.bp3-active{
            background:rgba(19, 124, 189, 0.3);
            color:#48aff0; }
          .bp3-dark .bp3-button.bp3-minimal.bp3-intent-primary:disabled, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-primary.bp3-disabled{
            background:none;
            color:rgba(72, 175, 240, 0.5); }
            .bp3-dark .bp3-button.bp3-minimal.bp3-intent-primary:disabled.bp3-active, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-primary.bp3-disabled.bp3-active{
              background:rgba(19, 124, 189, 0.3); }
      .bp3-button.bp3-minimal.bp3-intent-success{
        color:#0d8050; }
        .bp3-button.bp3-minimal.bp3-intent-success:hover, .bp3-button.bp3-minimal.bp3-intent-success:active, .bp3-button.bp3-minimal.bp3-intent-success.bp3-active{
          background:none;
          -webkit-box-shadow:none;
                  box-shadow:none;
          color:#0d8050; }
        .bp3-button.bp3-minimal.bp3-intent-success:hover{
          background:rgba(15, 153, 96, 0.15);
          color:#0d8050; }
        .bp3-button.bp3-minimal.bp3-intent-success:active, .bp3-button.bp3-minimal.bp3-intent-success.bp3-active{
          background:rgba(15, 153, 96, 0.3);
          color:#0d8050; }
        .bp3-button.bp3-minimal.bp3-intent-success:disabled, .bp3-button.bp3-minimal.bp3-intent-success.bp3-disabled{
          background:none;
          color:rgba(13, 128, 80, 0.5); }
          .bp3-button.bp3-minimal.bp3-intent-success:disabled.bp3-active, .bp3-button.bp3-minimal.bp3-intent-success.bp3-disabled.bp3-active{
            background:rgba(15, 153, 96, 0.3); }
        .bp3-button.bp3-minimal.bp3-intent-success .bp3-button-spinner .bp3-spinner-head{
          stroke:#0d8050; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-success{
          color:#3dcc91; }
          .bp3-dark .bp3-button.bp3-minimal.bp3-intent-success:hover{
            background:rgba(15, 153, 96, 0.2);
            color:#3dcc91; }
          .bp3-dark .bp3-button.bp3-minimal.bp3-intent-success:active, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-success.bp3-active{
            background:rgba(15, 153, 96, 0.3);
            color:#3dcc91; }
          .bp3-dark .bp3-button.bp3-minimal.bp3-intent-success:disabled, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-success.bp3-disabled{
            background:none;
            color:rgba(61, 204, 145, 0.5); }
            .bp3-dark .bp3-button.bp3-minimal.bp3-intent-success:disabled.bp3-active, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-success.bp3-disabled.bp3-active{
              background:rgba(15, 153, 96, 0.3); }
      .bp3-button.bp3-minimal.bp3-intent-warning{
        color:#bf7326; }
        .bp3-button.bp3-minimal.bp3-intent-warning:hover, .bp3-button.bp3-minimal.bp3-intent-warning:active, .bp3-button.bp3-minimal.bp3-intent-warning.bp3-active{
          background:none;
          -webkit-box-shadow:none;
                  box-shadow:none;
          color:#bf7326; }
        .bp3-button.bp3-minimal.bp3-intent-warning:hover{
          background:rgba(217, 130, 43, 0.15);
          color:#bf7326; }
        .bp3-button.bp3-minimal.bp3-intent-warning:active, .bp3-button.bp3-minimal.bp3-intent-warning.bp3-active{
          background:rgba(217, 130, 43, 0.3);
          color:#bf7326; }
        .bp3-button.bp3-minimal.bp3-intent-warning:disabled, .bp3-button.bp3-minimal.bp3-intent-warning.bp3-disabled{
          background:none;
          color:rgba(191, 115, 38, 0.5); }
          .bp3-button.bp3-minimal.bp3-intent-warning:disabled.bp3-active, .bp3-button.bp3-minimal.bp3-intent-warning.bp3-disabled.bp3-active{
            background:rgba(217, 130, 43, 0.3); }
        .bp3-button.bp3-minimal.bp3-intent-warning .bp3-button-spinner .bp3-spinner-head{
          stroke:#bf7326; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-warning{
          color:#ffb366; }
          .bp3-dark .bp3-button.bp3-minimal.bp3-intent-warning:hover{
            background:rgba(217, 130, 43, 0.2);
            color:#ffb366; }
          .bp3-dark .bp3-button.bp3-minimal.bp3-intent-warning:active, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-warning.bp3-active{
            background:rgba(217, 130, 43, 0.3);
            color:#ffb366; }
          .bp3-dark .bp3-button.bp3-minimal.bp3-intent-warning:disabled, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-warning.bp3-disabled{
            background:none;
            color:rgba(255, 179, 102, 0.5); }
            .bp3-dark .bp3-button.bp3-minimal.bp3-intent-warning:disabled.bp3-active, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-warning.bp3-disabled.bp3-active{
              background:rgba(217, 130, 43, 0.3); }
      .bp3-button.bp3-minimal.bp3-intent-danger{
        color:#c23030; }
        .bp3-button.bp3-minimal.bp3-intent-danger:hover, .bp3-button.bp3-minimal.bp3-intent-danger:active, .bp3-button.bp3-minimal.bp3-intent-danger.bp3-active{
          background:none;
          -webkit-box-shadow:none;
                  box-shadow:none;
          color:#c23030; }
        .bp3-button.bp3-minimal.bp3-intent-danger:hover{
          background:rgba(219, 55, 55, 0.15);
          color:#c23030; }
        .bp3-button.bp3-minimal.bp3-intent-danger:active, .bp3-button.bp3-minimal.bp3-intent-danger.bp3-active{
          background:rgba(219, 55, 55, 0.3);
          color:#c23030; }
        .bp3-button.bp3-minimal.bp3-intent-danger:disabled, .bp3-button.bp3-minimal.bp3-intent-danger.bp3-disabled{
          background:none;
          color:rgba(194, 48, 48, 0.5); }
          .bp3-button.bp3-minimal.bp3-intent-danger:disabled.bp3-active, .bp3-button.bp3-minimal.bp3-intent-danger.bp3-disabled.bp3-active{
            background:rgba(219, 55, 55, 0.3); }
        .bp3-button.bp3-minimal.bp3-intent-danger .bp3-button-spinner .bp3-spinner-head{
          stroke:#c23030; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-danger{
          color:#ff7373; }
          .bp3-dark .bp3-button.bp3-minimal.bp3-intent-danger:hover{
            background:rgba(219, 55, 55, 0.2);
            color:#ff7373; }
          .bp3-dark .bp3-button.bp3-minimal.bp3-intent-danger:active, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-danger.bp3-active{
            background:rgba(219, 55, 55, 0.3);
            color:#ff7373; }
          .bp3-dark .bp3-button.bp3-minimal.bp3-intent-danger:disabled, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-danger.bp3-disabled{
            background:none;
            color:rgba(255, 115, 115, 0.5); }
            .bp3-dark .bp3-button.bp3-minimal.bp3-intent-danger:disabled.bp3-active, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-danger.bp3-disabled.bp3-active{
              background:rgba(219, 55, 55, 0.3); }
    .bp3-button.bp3-outlined{
      background:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      border:1px solid rgba(24, 32, 38, 0.2);
      -webkit-box-sizing:border-box;
              box-sizing:border-box; }
      .bp3-button.bp3-outlined:hover{
        background:rgba(167, 182, 194, 0.3);
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#182026;
        text-decoration:none; }
      .bp3-button.bp3-outlined:active, .bp3-button.bp3-outlined.bp3-active{
        background:rgba(115, 134, 148, 0.3);
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#182026; }
      .bp3-button.bp3-outlined:disabled, .bp3-button.bp3-outlined:disabled:hover, .bp3-button.bp3-outlined.bp3-disabled, .bp3-button.bp3-outlined.bp3-disabled:hover{
        background:none;
        color:rgba(92, 112, 128, 0.6);
        cursor:not-allowed; }
        .bp3-button.bp3-outlined:disabled.bp3-active, .bp3-button.bp3-outlined:disabled:hover.bp3-active, .bp3-button.bp3-outlined.bp3-disabled.bp3-active, .bp3-button.bp3-outlined.bp3-disabled:hover.bp3-active{
          background:rgba(115, 134, 148, 0.3); }
      .bp3-dark .bp3-button.bp3-outlined{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:inherit; }
        .bp3-dark .bp3-button.bp3-outlined:hover, .bp3-dark .bp3-button.bp3-outlined:active, .bp3-dark .bp3-button.bp3-outlined.bp3-active{
          background:none;
          -webkit-box-shadow:none;
                  box-shadow:none; }
        .bp3-dark .bp3-button.bp3-outlined:hover{
          background:rgba(138, 155, 168, 0.15); }
        .bp3-dark .bp3-button.bp3-outlined:active, .bp3-dark .bp3-button.bp3-outlined.bp3-active{
          background:rgba(138, 155, 168, 0.3);
          color:#f5f8fa; }
        .bp3-dark .bp3-button.bp3-outlined:disabled, .bp3-dark .bp3-button.bp3-outlined:disabled:hover, .bp3-dark .bp3-button.bp3-outlined.bp3-disabled, .bp3-dark .bp3-button.bp3-outlined.bp3-disabled:hover{
          background:none;
          color:rgba(167, 182, 194, 0.6);
          cursor:not-allowed; }
          .bp3-dark .bp3-button.bp3-outlined:disabled.bp3-active, .bp3-dark .bp3-button.bp3-outlined:disabled:hover.bp3-active, .bp3-dark .bp3-button.bp3-outlined.bp3-disabled.bp3-active, .bp3-dark .bp3-button.bp3-outlined.bp3-disabled:hover.bp3-active{
            background:rgba(138, 155, 168, 0.3); }
      .bp3-button.bp3-outlined.bp3-intent-primary{
        color:#106ba3; }
        .bp3-button.bp3-outlined.bp3-intent-primary:hover, .bp3-button.bp3-outlined.bp3-intent-primary:active, .bp3-button.bp3-outlined.bp3-intent-primary.bp3-active{
          background:none;
          -webkit-box-shadow:none;
                  box-shadow:none;
          color:#106ba3; }
        .bp3-button.bp3-outlined.bp3-intent-primary:hover{
          background:rgba(19, 124, 189, 0.15);
          color:#106ba3; }
        .bp3-button.bp3-outlined.bp3-intent-primary:active, .bp3-button.bp3-outlined.bp3-intent-primary.bp3-active{
          background:rgba(19, 124, 189, 0.3);
          color:#106ba3; }
        .bp3-button.bp3-outlined.bp3-intent-primary:disabled, .bp3-button.bp3-outlined.bp3-intent-primary.bp3-disabled{
          background:none;
          color:rgba(16, 107, 163, 0.5); }
          .bp3-button.bp3-outlined.bp3-intent-primary:disabled.bp3-active, .bp3-button.bp3-outlined.bp3-intent-primary.bp3-disabled.bp3-active{
            background:rgba(19, 124, 189, 0.3); }
        .bp3-button.bp3-outlined.bp3-intent-primary .bp3-button-spinner .bp3-spinner-head{
          stroke:#106ba3; }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary{
          color:#48aff0; }
          .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary:hover{
            background:rgba(19, 124, 189, 0.2);
            color:#48aff0; }
          .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary:active, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary.bp3-active{
            background:rgba(19, 124, 189, 0.3);
            color:#48aff0; }
          .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary:disabled, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary.bp3-disabled{
            background:none;
            color:rgba(72, 175, 240, 0.5); }
            .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary:disabled.bp3-active, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary.bp3-disabled.bp3-active{
              background:rgba(19, 124, 189, 0.3); }
      .bp3-button.bp3-outlined.bp3-intent-success{
        color:#0d8050; }
        .bp3-button.bp3-outlined.bp3-intent-success:hover, .bp3-button.bp3-outlined.bp3-intent-success:active, .bp3-button.bp3-outlined.bp3-intent-success.bp3-active{
          background:none;
          -webkit-box-shadow:none;
                  box-shadow:none;
          color:#0d8050; }
        .bp3-button.bp3-outlined.bp3-intent-success:hover{
          background:rgba(15, 153, 96, 0.15);
          color:#0d8050; }
        .bp3-button.bp3-outlined.bp3-intent-success:active, .bp3-button.bp3-outlined.bp3-intent-success.bp3-active{
          background:rgba(15, 153, 96, 0.3);
          color:#0d8050; }
        .bp3-button.bp3-outlined.bp3-intent-success:disabled, .bp3-button.bp3-outlined.bp3-intent-success.bp3-disabled{
          background:none;
          color:rgba(13, 128, 80, 0.5); }
          .bp3-button.bp3-outlined.bp3-intent-success:disabled.bp3-active, .bp3-button.bp3-outlined.bp3-intent-success.bp3-disabled.bp3-active{
            background:rgba(15, 153, 96, 0.3); }
        .bp3-button.bp3-outlined.bp3-intent-success .bp3-button-spinner .bp3-spinner-head{
          stroke:#0d8050; }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success{
          color:#3dcc91; }
          .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success:hover{
            background:rgba(15, 153, 96, 0.2);
            color:#3dcc91; }
          .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success:active, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success.bp3-active{
            background:rgba(15, 153, 96, 0.3);
            color:#3dcc91; }
          .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success:disabled, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success.bp3-disabled{
            background:none;
            color:rgba(61, 204, 145, 0.5); }
            .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success:disabled.bp3-active, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success.bp3-disabled.bp3-active{
              background:rgba(15, 153, 96, 0.3); }
      .bp3-button.bp3-outlined.bp3-intent-warning{
        color:#bf7326; }
        .bp3-button.bp3-outlined.bp3-intent-warning:hover, .bp3-button.bp3-outlined.bp3-intent-warning:active, .bp3-button.bp3-outlined.bp3-intent-warning.bp3-active{
          background:none;
          -webkit-box-shadow:none;
                  box-shadow:none;
          color:#bf7326; }
        .bp3-button.bp3-outlined.bp3-intent-warning:hover{
          background:rgba(217, 130, 43, 0.15);
          color:#bf7326; }
        .bp3-button.bp3-outlined.bp3-intent-warning:active, .bp3-button.bp3-outlined.bp3-intent-warning.bp3-active{
          background:rgba(217, 130, 43, 0.3);
          color:#bf7326; }
        .bp3-button.bp3-outlined.bp3-intent-warning:disabled, .bp3-button.bp3-outlined.bp3-intent-warning.bp3-disabled{
          background:none;
          color:rgba(191, 115, 38, 0.5); }
          .bp3-button.bp3-outlined.bp3-intent-warning:disabled.bp3-active, .bp3-button.bp3-outlined.bp3-intent-warning.bp3-disabled.bp3-active{
            background:rgba(217, 130, 43, 0.3); }
        .bp3-button.bp3-outlined.bp3-intent-warning .bp3-button-spinner .bp3-spinner-head{
          stroke:#bf7326; }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning{
          color:#ffb366; }
          .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning:hover{
            background:rgba(217, 130, 43, 0.2);
            color:#ffb366; }
          .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning:active, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning.bp3-active{
            background:rgba(217, 130, 43, 0.3);
            color:#ffb366; }
          .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning:disabled, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning.bp3-disabled{
            background:none;
            color:rgba(255, 179, 102, 0.5); }
            .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning:disabled.bp3-active, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning.bp3-disabled.bp3-active{
              background:rgba(217, 130, 43, 0.3); }
      .bp3-button.bp3-outlined.bp3-intent-danger{
        color:#c23030; }
        .bp3-button.bp3-outlined.bp3-intent-danger:hover, .bp3-button.bp3-outlined.bp3-intent-danger:active, .bp3-button.bp3-outlined.bp3-intent-danger.bp3-active{
          background:none;
          -webkit-box-shadow:none;
                  box-shadow:none;
          color:#c23030; }
        .bp3-button.bp3-outlined.bp3-intent-danger:hover{
          background:rgba(219, 55, 55, 0.15);
          color:#c23030; }
        .bp3-button.bp3-outlined.bp3-intent-danger:active, .bp3-button.bp3-outlined.bp3-intent-danger.bp3-active{
          background:rgba(219, 55, 55, 0.3);
          color:#c23030; }
        .bp3-button.bp3-outlined.bp3-intent-danger:disabled, .bp3-button.bp3-outlined.bp3-intent-danger.bp3-disabled{
          background:none;
          color:rgba(194, 48, 48, 0.5); }
          .bp3-button.bp3-outlined.bp3-intent-danger:disabled.bp3-active, .bp3-button.bp3-outlined.bp3-intent-danger.bp3-disabled.bp3-active{
            background:rgba(219, 55, 55, 0.3); }
        .bp3-button.bp3-outlined.bp3-intent-danger .bp3-button-spinner .bp3-spinner-head{
          stroke:#c23030; }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger{
          color:#ff7373; }
          .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger:hover{
            background:rgba(219, 55, 55, 0.2);
            color:#ff7373; }
          .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger:active, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger.bp3-active{
            background:rgba(219, 55, 55, 0.3);
            color:#ff7373; }
          .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger:disabled, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger.bp3-disabled{
            background:none;
            color:rgba(255, 115, 115, 0.5); }
            .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger:disabled.bp3-active, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger.bp3-disabled.bp3-active{
              background:rgba(219, 55, 55, 0.3); }
      .bp3-button.bp3-outlined:disabled, .bp3-button.bp3-outlined.bp3-disabled, .bp3-button.bp3-outlined:disabled:hover, .bp3-button.bp3-outlined.bp3-disabled:hover{
        border-color:rgba(92, 112, 128, 0.1); }
      .bp3-dark .bp3-button.bp3-outlined{
        border-color:rgba(255, 255, 255, 0.4); }
        .bp3-dark .bp3-button.bp3-outlined:disabled, .bp3-dark .bp3-button.bp3-outlined:disabled:hover, .bp3-dark .bp3-button.bp3-outlined.bp3-disabled, .bp3-dark .bp3-button.bp3-outlined.bp3-disabled:hover{
          border-color:rgba(255, 255, 255, 0.2); }
      .bp3-button.bp3-outlined.bp3-intent-primary{
        border-color:rgba(16, 107, 163, 0.6); }
        .bp3-button.bp3-outlined.bp3-intent-primary:disabled, .bp3-button.bp3-outlined.bp3-intent-primary.bp3-disabled{
          border-color:rgba(16, 107, 163, 0.2); }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary{
          border-color:rgba(72, 175, 240, 0.6); }
          .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary:disabled, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary.bp3-disabled{
            border-color:rgba(72, 175, 240, 0.2); }
      .bp3-button.bp3-outlined.bp3-intent-success{
        border-color:rgba(13, 128, 80, 0.6); }
        .bp3-button.bp3-outlined.bp3-intent-success:disabled, .bp3-button.bp3-outlined.bp3-intent-success.bp3-disabled{
          border-color:rgba(13, 128, 80, 0.2); }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success{
          border-color:rgba(61, 204, 145, 0.6); }
          .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success:disabled, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success.bp3-disabled{
            border-color:rgba(61, 204, 145, 0.2); }
      .bp3-button.bp3-outlined.bp3-intent-warning{
        border-color:rgba(191, 115, 38, 0.6); }
        .bp3-button.bp3-outlined.bp3-intent-warning:disabled, .bp3-button.bp3-outlined.bp3-intent-warning.bp3-disabled{
          border-color:rgba(191, 115, 38, 0.2); }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning{
          border-color:rgba(255, 179, 102, 0.6); }
          .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning:disabled, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning.bp3-disabled{
            border-color:rgba(255, 179, 102, 0.2); }
      .bp3-button.bp3-outlined.bp3-intent-danger{
        border-color:rgba(194, 48, 48, 0.6); }
        .bp3-button.bp3-outlined.bp3-intent-danger:disabled, .bp3-button.bp3-outlined.bp3-intent-danger.bp3-disabled{
          border-color:rgba(194, 48, 48, 0.2); }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger{
          border-color:rgba(255, 115, 115, 0.6); }
          .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger:disabled, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger.bp3-disabled{
            border-color:rgba(255, 115, 115, 0.2); }

  a.bp3-button{
    text-align:center;
    text-decoration:none;
    -webkit-transition:none;
    transition:none; }
    a.bp3-button, a.bp3-button:hover, a.bp3-button:active{
      color:#182026; }
    a.bp3-button.bp3-disabled{
      color:rgba(92, 112, 128, 0.6); }

  .bp3-button-text{
    -webkit-box-flex:0;
        -ms-flex:0 1 auto;
            flex:0 1 auto; }

  .bp3-button.bp3-align-left .bp3-button-text, .bp3-button.bp3-align-right .bp3-button-text,
  .bp3-button-group.bp3-align-left .bp3-button-text,
  .bp3-button-group.bp3-align-right .bp3-button-text{
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto; }
  .bp3-button-group{
    display:-webkit-inline-box;
    display:-ms-inline-flexbox;
    display:inline-flex; }
    .bp3-button-group .bp3-button{
      -webkit-box-flex:0;
          -ms-flex:0 0 auto;
              flex:0 0 auto;
      position:relative;
      z-index:4; }
      .bp3-button-group .bp3-button:focus{
        z-index:5; }
      .bp3-button-group .bp3-button:hover{
        z-index:6; }
      .bp3-button-group .bp3-button:active, .bp3-button-group .bp3-button.bp3-active{
        z-index:7; }
      .bp3-button-group .bp3-button:disabled, .bp3-button-group .bp3-button.bp3-disabled{
        z-index:3; }
      .bp3-button-group .bp3-button[class*="bp3-intent-"]{
        z-index:9; }
        .bp3-button-group .bp3-button[class*="bp3-intent-"]:focus{
          z-index:10; }
        .bp3-button-group .bp3-button[class*="bp3-intent-"]:hover{
          z-index:11; }
        .bp3-button-group .bp3-button[class*="bp3-intent-"]:active, .bp3-button-group .bp3-button[class*="bp3-intent-"].bp3-active{
          z-index:12; }
        .bp3-button-group .bp3-button[class*="bp3-intent-"]:disabled, .bp3-button-group .bp3-button[class*="bp3-intent-"].bp3-disabled{
          z-index:8; }
    .bp3-button-group:not(.bp3-minimal) > .bp3-popover-wrapper:not(:first-child) .bp3-button,
    .bp3-button-group:not(.bp3-minimal) > .bp3-button:not(:first-child){
      border-bottom-left-radius:0;
      border-top-left-radius:0; }
    .bp3-button-group:not(.bp3-minimal) > .bp3-popover-wrapper:not(:last-child) .bp3-button,
    .bp3-button-group:not(.bp3-minimal) > .bp3-button:not(:last-child){
      border-bottom-right-radius:0;
      border-top-right-radius:0;
      margin-right:-1px; }
    .bp3-button-group.bp3-minimal .bp3-button{
      background:none;
      -webkit-box-shadow:none;
              box-shadow:none; }
      .bp3-button-group.bp3-minimal .bp3-button:hover{
        background:rgba(167, 182, 194, 0.3);
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#182026;
        text-decoration:none; }
      .bp3-button-group.bp3-minimal .bp3-button:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-active{
        background:rgba(115, 134, 148, 0.3);
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#182026; }
      .bp3-button-group.bp3-minimal .bp3-button:disabled, .bp3-button-group.bp3-minimal .bp3-button:disabled:hover, .bp3-button-group.bp3-minimal .bp3-button.bp3-disabled, .bp3-button-group.bp3-minimal .bp3-button.bp3-disabled:hover{
        background:none;
        color:rgba(92, 112, 128, 0.6);
        cursor:not-allowed; }
        .bp3-button-group.bp3-minimal .bp3-button:disabled.bp3-active, .bp3-button-group.bp3-minimal .bp3-button:disabled:hover.bp3-active, .bp3-button-group.bp3-minimal .bp3-button.bp3-disabled.bp3-active, .bp3-button-group.bp3-minimal .bp3-button.bp3-disabled:hover.bp3-active{
          background:rgba(115, 134, 148, 0.3); }
      .bp3-dark .bp3-button-group.bp3-minimal .bp3-button{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:inherit; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button:hover, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button:active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-active{
          background:none;
          -webkit-box-shadow:none;
                  box-shadow:none; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button:hover{
          background:rgba(138, 155, 168, 0.15); }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button:active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-active{
          background:rgba(138, 155, 168, 0.3);
          color:#f5f8fa; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button:disabled, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button:disabled:hover, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-disabled, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-disabled:hover{
          background:none;
          color:rgba(167, 182, 194, 0.6);
          cursor:not-allowed; }
          .bp3-dark .bp3-button-group.bp3-minimal .bp3-button:disabled.bp3-active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button:disabled:hover.bp3-active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-disabled.bp3-active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-disabled:hover.bp3-active{
            background:rgba(138, 155, 168, 0.3); }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary{
        color:#106ba3; }
        .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:hover, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary.bp3-active{
          background:none;
          -webkit-box-shadow:none;
                  box-shadow:none;
          color:#106ba3; }
        .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:hover{
          background:rgba(19, 124, 189, 0.15);
          color:#106ba3; }
        .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary.bp3-active{
          background:rgba(19, 124, 189, 0.3);
          color:#106ba3; }
        .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:disabled, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary.bp3-disabled{
          background:none;
          color:rgba(16, 107, 163, 0.5); }
          .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:disabled.bp3-active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary.bp3-disabled.bp3-active{
            background:rgba(19, 124, 189, 0.3); }
        .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary .bp3-button-spinner .bp3-spinner-head{
          stroke:#106ba3; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary{
          color:#48aff0; }
          .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:hover{
            background:rgba(19, 124, 189, 0.2);
            color:#48aff0; }
          .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary.bp3-active{
            background:rgba(19, 124, 189, 0.3);
            color:#48aff0; }
          .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:disabled, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary.bp3-disabled{
            background:none;
            color:rgba(72, 175, 240, 0.5); }
            .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:disabled.bp3-active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary.bp3-disabled.bp3-active{
              background:rgba(19, 124, 189, 0.3); }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success{
        color:#0d8050; }
        .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:hover, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success.bp3-active{
          background:none;
          -webkit-box-shadow:none;
                  box-shadow:none;
          color:#0d8050; }
        .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:hover{
          background:rgba(15, 153, 96, 0.15);
          color:#0d8050; }
        .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success.bp3-active{
          background:rgba(15, 153, 96, 0.3);
          color:#0d8050; }
        .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:disabled, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success.bp3-disabled{
          background:none;
          color:rgba(13, 128, 80, 0.5); }
          .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:disabled.bp3-active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success.bp3-disabled.bp3-active{
            background:rgba(15, 153, 96, 0.3); }
        .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success .bp3-button-spinner .bp3-spinner-head{
          stroke:#0d8050; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success{
          color:#3dcc91; }
          .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:hover{
            background:rgba(15, 153, 96, 0.2);
            color:#3dcc91; }
          .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success.bp3-active{
            background:rgba(15, 153, 96, 0.3);
            color:#3dcc91; }
          .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:disabled, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success.bp3-disabled{
            background:none;
            color:rgba(61, 204, 145, 0.5); }
            .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:disabled.bp3-active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success.bp3-disabled.bp3-active{
              background:rgba(15, 153, 96, 0.3); }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning{
        color:#bf7326; }
        .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:hover, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning.bp3-active{
          background:none;
          -webkit-box-shadow:none;
                  box-shadow:none;
          color:#bf7326; }
        .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:hover{
          background:rgba(217, 130, 43, 0.15);
          color:#bf7326; }
        .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning.bp3-active{
          background:rgba(217, 130, 43, 0.3);
          color:#bf7326; }
        .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:disabled, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning.bp3-disabled{
          background:none;
          color:rgba(191, 115, 38, 0.5); }
          .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:disabled.bp3-active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning.bp3-disabled.bp3-active{
            background:rgba(217, 130, 43, 0.3); }
        .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning .bp3-button-spinner .bp3-spinner-head{
          stroke:#bf7326; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning{
          color:#ffb366; }
          .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:hover{
            background:rgba(217, 130, 43, 0.2);
            color:#ffb366; }
          .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning.bp3-active{
            background:rgba(217, 130, 43, 0.3);
            color:#ffb366; }
          .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:disabled, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning.bp3-disabled{
            background:none;
            color:rgba(255, 179, 102, 0.5); }
            .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:disabled.bp3-active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning.bp3-disabled.bp3-active{
              background:rgba(217, 130, 43, 0.3); }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger{
        color:#c23030; }
        .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:hover, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger.bp3-active{
          background:none;
          -webkit-box-shadow:none;
                  box-shadow:none;
          color:#c23030; }
        .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:hover{
          background:rgba(219, 55, 55, 0.15);
          color:#c23030; }
        .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger.bp3-active{
          background:rgba(219, 55, 55, 0.3);
          color:#c23030; }
        .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:disabled, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger.bp3-disabled{
          background:none;
          color:rgba(194, 48, 48, 0.5); }
          .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:disabled.bp3-active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger.bp3-disabled.bp3-active{
            background:rgba(219, 55, 55, 0.3); }
        .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger .bp3-button-spinner .bp3-spinner-head{
          stroke:#c23030; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger{
          color:#ff7373; }
          .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:hover{
            background:rgba(219, 55, 55, 0.2);
            color:#ff7373; }
          .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger.bp3-active{
            background:rgba(219, 55, 55, 0.3);
            color:#ff7373; }
          .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:disabled, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger.bp3-disabled{
            background:none;
            color:rgba(255, 115, 115, 0.5); }
            .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:disabled.bp3-active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger.bp3-disabled.bp3-active{
              background:rgba(219, 55, 55, 0.3); }
    .bp3-button-group .bp3-popover-wrapper,
    .bp3-button-group .bp3-popover-target{
      display:-webkit-box;
      display:-ms-flexbox;
      display:flex;
      -webkit-box-flex:1;
          -ms-flex:1 1 auto;
              flex:1 1 auto; }
    .bp3-button-group.bp3-fill{
      display:-webkit-box;
      display:-ms-flexbox;
      display:flex;
      width:100%; }
    .bp3-button-group .bp3-button.bp3-fill,
    .bp3-button-group.bp3-fill .bp3-button:not(.bp3-fixed){
      -webkit-box-flex:1;
          -ms-flex:1 1 auto;
              flex:1 1 auto; }
    .bp3-button-group.bp3-vertical{
      -webkit-box-align:stretch;
          -ms-flex-align:stretch;
              align-items:stretch;
      -webkit-box-orient:vertical;
      -webkit-box-direction:normal;
          -ms-flex-direction:column;
              flex-direction:column;
      vertical-align:top; }
      .bp3-button-group.bp3-vertical.bp3-fill{
        height:100%;
        width:unset; }
      .bp3-button-group.bp3-vertical .bp3-button{
        margin-right:0 !important;
        width:100%; }
      .bp3-button-group.bp3-vertical:not(.bp3-minimal) > .bp3-popover-wrapper:first-child .bp3-button,
      .bp3-button-group.bp3-vertical:not(.bp3-minimal) > .bp3-button:first-child{
        border-radius:3px 3px 0 0; }
      .bp3-button-group.bp3-vertical:not(.bp3-minimal) > .bp3-popover-wrapper:last-child .bp3-button,
      .bp3-button-group.bp3-vertical:not(.bp3-minimal) > .bp3-button:last-child{
        border-radius:0 0 3px 3px; }
      .bp3-button-group.bp3-vertical:not(.bp3-minimal) > .bp3-popover-wrapper:not(:last-child) .bp3-button,
      .bp3-button-group.bp3-vertical:not(.bp3-minimal) > .bp3-button:not(:last-child){
        margin-bottom:-1px; }
    .bp3-button-group.bp3-align-left .bp3-button{
      text-align:left; }
    .bp3-dark .bp3-button-group:not(.bp3-minimal) > .bp3-popover-wrapper:not(:last-child) .bp3-button,
    .bp3-dark .bp3-button-group:not(.bp3-minimal) > .bp3-button:not(:last-child){
      margin-right:1px; }
    .bp3-dark .bp3-button-group.bp3-vertical > .bp3-popover-wrapper:not(:last-child) .bp3-button,
    .bp3-dark .bp3-button-group.bp3-vertical > .bp3-button:not(:last-child){
      margin-bottom:1px; }
  .bp3-callout{
    font-size:14px;
    line-height:1.5;
    background-color:rgba(138, 155, 168, 0.15);
    border-radius:3px;
    padding:10px 12px 9px;
    position:relative;
    width:100%; }
    .bp3-callout[class*="bp3-icon-"]{
      padding-left:40px; }
      .bp3-callout[class*="bp3-icon-"]::before{
        font-family:"Icons20", sans-serif;
        font-size:20px;
        font-style:normal;
        font-weight:400;
        line-height:1;
        -moz-osx-font-smoothing:grayscale;
        -webkit-font-smoothing:antialiased;
        color:#5c7080;
        left:10px;
        position:absolute;
        top:10px; }
    .bp3-callout.bp3-callout-icon{
      padding-left:40px; }
      .bp3-callout.bp3-callout-icon > .bp3-icon:first-child{
        color:#5c7080;
        left:10px;
        position:absolute;
        top:10px; }
    .bp3-callout .bp3-heading{
      line-height:20px;
      margin-bottom:5px;
      margin-top:0; }
      .bp3-callout .bp3-heading:last-child{
        margin-bottom:0; }
    .bp3-dark .bp3-callout{
      background-color:rgba(138, 155, 168, 0.2); }
      .bp3-dark .bp3-callout[class*="bp3-icon-"]::before{
        color:#a7b6c2; }
    .bp3-callout.bp3-intent-primary{
      background-color:rgba(19, 124, 189, 0.15); }
      .bp3-callout.bp3-intent-primary[class*="bp3-icon-"]::before,
      .bp3-callout.bp3-intent-primary > .bp3-icon:first-child,
      .bp3-callout.bp3-intent-primary .bp3-heading{
        color:#106ba3; }
      .bp3-dark .bp3-callout.bp3-intent-primary{
        background-color:rgba(19, 124, 189, 0.25); }
        .bp3-dark .bp3-callout.bp3-intent-primary[class*="bp3-icon-"]::before,
        .bp3-dark .bp3-callout.bp3-intent-primary > .bp3-icon:first-child,
        .bp3-dark .bp3-callout.bp3-intent-primary .bp3-heading{
          color:#48aff0; }
    .bp3-callout.bp3-intent-success{
      background-color:rgba(15, 153, 96, 0.15); }
      .bp3-callout.bp3-intent-success[class*="bp3-icon-"]::before,
      .bp3-callout.bp3-intent-success > .bp3-icon:first-child,
      .bp3-callout.bp3-intent-success .bp3-heading{
        color:#0d8050; }
      .bp3-dark .bp3-callout.bp3-intent-success{
        background-color:rgba(15, 153, 96, 0.25); }
        .bp3-dark .bp3-callout.bp3-intent-success[class*="bp3-icon-"]::before,
        .bp3-dark .bp3-callout.bp3-intent-success > .bp3-icon:first-child,
        .bp3-dark .bp3-callout.bp3-intent-success .bp3-heading{
          color:#3dcc91; }
    .bp3-callout.bp3-intent-warning{
      background-color:rgba(217, 130, 43, 0.15); }
      .bp3-callout.bp3-intent-warning[class*="bp3-icon-"]::before,
      .bp3-callout.bp3-intent-warning > .bp3-icon:first-child,
      .bp3-callout.bp3-intent-warning .bp3-heading{
        color:#bf7326; }
      .bp3-dark .bp3-callout.bp3-intent-warning{
        background-color:rgba(217, 130, 43, 0.25); }
        .bp3-dark .bp3-callout.bp3-intent-warning[class*="bp3-icon-"]::before,
        .bp3-dark .bp3-callout.bp3-intent-warning > .bp3-icon:first-child,
        .bp3-dark .bp3-callout.bp3-intent-warning .bp3-heading{
          color:#ffb366; }
    .bp3-callout.bp3-intent-danger{
      background-color:rgba(219, 55, 55, 0.15); }
      .bp3-callout.bp3-intent-danger[class*="bp3-icon-"]::before,
      .bp3-callout.bp3-intent-danger > .bp3-icon:first-child,
      .bp3-callout.bp3-intent-danger .bp3-heading{
        color:#c23030; }
      .bp3-dark .bp3-callout.bp3-intent-danger{
        background-color:rgba(219, 55, 55, 0.25); }
        .bp3-dark .bp3-callout.bp3-intent-danger[class*="bp3-icon-"]::before,
        .bp3-dark .bp3-callout.bp3-intent-danger > .bp3-icon:first-child,
        .bp3-dark .bp3-callout.bp3-intent-danger .bp3-heading{
          color:#ff7373; }
    .bp3-running-text .bp3-callout{
      margin:20px 0; }
  .bp3-card{
    background-color:#ffffff;
    border-radius:3px;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.15), 0 0 0 rgba(16, 22, 26, 0), 0 0 0 rgba(16, 22, 26, 0);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.15), 0 0 0 rgba(16, 22, 26, 0), 0 0 0 rgba(16, 22, 26, 0);
    padding:20px;
    -webkit-transition:-webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-box-shadow 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:-webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-box-shadow 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9), box-shadow 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9), box-shadow 200ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-box-shadow 200ms cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-card.bp3-dark,
    .bp3-dark .bp3-card{
      background-color:#30404d;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), 0 0 0 rgba(16, 22, 26, 0), 0 0 0 rgba(16, 22, 26, 0);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), 0 0 0 rgba(16, 22, 26, 0), 0 0 0 rgba(16, 22, 26, 0); }

  .bp3-elevation-0{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.15), 0 0 0 rgba(16, 22, 26, 0), 0 0 0 rgba(16, 22, 26, 0);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.15), 0 0 0 rgba(16, 22, 26, 0), 0 0 0 rgba(16, 22, 26, 0); }
    .bp3-elevation-0.bp3-dark,
    .bp3-dark .bp3-elevation-0{
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), 0 0 0 rgba(16, 22, 26, 0), 0 0 0 rgba(16, 22, 26, 0);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), 0 0 0 rgba(16, 22, 26, 0), 0 0 0 rgba(16, 22, 26, 0); }

  .bp3-elevation-1{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-elevation-1.bp3-dark,
    .bp3-dark .bp3-elevation-1{
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4); }

  .bp3-elevation-2{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 1px 1px rgba(16, 22, 26, 0.2), 0 2px 6px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 1px 1px rgba(16, 22, 26, 0.2), 0 2px 6px rgba(16, 22, 26, 0.2); }
    .bp3-elevation-2.bp3-dark,
    .bp3-dark .bp3-elevation-2{
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 1px 1px rgba(16, 22, 26, 0.4), 0 2px 6px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 1px 1px rgba(16, 22, 26, 0.4), 0 2px 6px rgba(16, 22, 26, 0.4); }

  .bp3-elevation-3{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2); }
    .bp3-elevation-3.bp3-dark,
    .bp3-dark .bp3-elevation-3{
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4); }

  .bp3-elevation-4{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 4px 8px rgba(16, 22, 26, 0.2), 0 18px 46px 6px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 4px 8px rgba(16, 22, 26, 0.2), 0 18px 46px 6px rgba(16, 22, 26, 0.2); }
    .bp3-elevation-4.bp3-dark,
    .bp3-dark .bp3-elevation-4{
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 4px 8px rgba(16, 22, 26, 0.4), 0 18px 46px 6px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 4px 8px rgba(16, 22, 26, 0.4), 0 18px 46px 6px rgba(16, 22, 26, 0.4); }

  .bp3-card.bp3-interactive:hover{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
    cursor:pointer; }
    .bp3-card.bp3-interactive:hover.bp3-dark,
    .bp3-dark .bp3-card.bp3-interactive:hover{
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4); }

  .bp3-card.bp3-interactive:active{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.2);
    opacity:0.9;
    -webkit-transition-duration:0;
            transition-duration:0; }
    .bp3-card.bp3-interactive:active.bp3-dark,
    .bp3-dark .bp3-card.bp3-interactive:active{
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4); }

  .bp3-collapse{
    height:0;
    overflow-y:hidden;
    -webkit-transition:height 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:height 200ms cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-collapse .bp3-collapse-body{
      -webkit-transition:-webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
      transition:-webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
      transition:transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
      transition:transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9); }
      .bp3-collapse .bp3-collapse-body[aria-hidden="true"]{
        display:none; }

  .bp3-context-menu .bp3-popover-target{
    display:block; }

  .bp3-context-menu-popover-target{
    position:fixed; }

  .bp3-divider{
    border-bottom:1px solid rgba(16, 22, 26, 0.15);
    border-right:1px solid rgba(16, 22, 26, 0.15);
    margin:5px; }
    .bp3-dark .bp3-divider{
      border-color:rgba(16, 22, 26, 0.4); }
  .bp3-dialog-container{
    opacity:1;
    -webkit-transform:scale(1);
            transform:scale(1);
    -webkit-box-align:center;
        -ms-flex-align:center;
            align-items:center;
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    -webkit-box-pack:center;
        -ms-flex-pack:center;
            justify-content:center;
    min-height:100%;
    pointer-events:none;
    -webkit-user-select:none;
      -moz-user-select:none;
        -ms-user-select:none;
            user-select:none;
    width:100%; }
    .bp3-dialog-container.bp3-overlay-enter > .bp3-dialog, .bp3-dialog-container.bp3-overlay-appear > .bp3-dialog{
      opacity:0;
      -webkit-transform:scale(0.5);
              transform:scale(0.5); }
    .bp3-dialog-container.bp3-overlay-enter-active > .bp3-dialog, .bp3-dialog-container.bp3-overlay-appear-active > .bp3-dialog{
      opacity:1;
      -webkit-transform:scale(1);
              transform:scale(1);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:300ms;
              transition-duration:300ms;
      -webkit-transition-property:opacity, -webkit-transform;
      transition-property:opacity, -webkit-transform;
      transition-property:opacity, transform;
      transition-property:opacity, transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11);
              transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11); }
    .bp3-dialog-container.bp3-overlay-exit > .bp3-dialog{
      opacity:1;
      -webkit-transform:scale(1);
              transform:scale(1); }
    .bp3-dialog-container.bp3-overlay-exit-active > .bp3-dialog{
      opacity:0;
      -webkit-transform:scale(0.5);
              transform:scale(0.5);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:300ms;
              transition-duration:300ms;
      -webkit-transition-property:opacity, -webkit-transform;
      transition-property:opacity, -webkit-transform;
      transition-property:opacity, transform;
      transition-property:opacity, transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11);
              transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11); }

  .bp3-dialog{
    background:#ebf1f5;
    border-radius:6px;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 4px 8px rgba(16, 22, 26, 0.2), 0 18px 46px 6px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 4px 8px rgba(16, 22, 26, 0.2), 0 18px 46px 6px rgba(16, 22, 26, 0.2);
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    -webkit-box-orient:vertical;
    -webkit-box-direction:normal;
        -ms-flex-direction:column;
            flex-direction:column;
    margin:30px 0;
    padding-bottom:20px;
    pointer-events:all;
    -webkit-user-select:text;
      -moz-user-select:text;
        -ms-user-select:text;
            user-select:text;
    width:500px; }
    .bp3-dialog:focus{
      outline:0; }
    .bp3-dialog.bp3-dark,
    .bp3-dark .bp3-dialog{
      background:#293742;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 4px 8px rgba(16, 22, 26, 0.4), 0 18px 46px 6px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 4px 8px rgba(16, 22, 26, 0.4), 0 18px 46px 6px rgba(16, 22, 26, 0.4);
      color:#f5f8fa; }

  .bp3-dialog-header{
    -webkit-box-align:center;
        -ms-flex-align:center;
            align-items:center;
    background:#ffffff;
    border-radius:6px 6px 0 0;
    -webkit-box-shadow:0 1px 0 rgba(16, 22, 26, 0.15);
            box-shadow:0 1px 0 rgba(16, 22, 26, 0.15);
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    -webkit-box-flex:0;
        -ms-flex:0 0 auto;
            flex:0 0 auto;
    min-height:40px;
    padding-left:20px;
    padding-right:5px; }
    .bp3-dialog-header .bp3-icon-large,
    .bp3-dialog-header .bp3-icon{
      color:#5c7080;
      -webkit-box-flex:0;
          -ms-flex:0 0 auto;
              flex:0 0 auto;
      margin-right:10px; }
    .bp3-dialog-header .bp3-heading{
      overflow:hidden;
      text-overflow:ellipsis;
      white-space:nowrap;
      word-wrap:normal;
      -webkit-box-flex:1;
          -ms-flex:1 1 auto;
              flex:1 1 auto;
      line-height:inherit;
      margin:0; }
      .bp3-dialog-header .bp3-heading:last-child{
        margin-right:20px; }
    .bp3-dark .bp3-dialog-header{
      background:#30404d;
      -webkit-box-shadow:0 1px 0 rgba(16, 22, 26, 0.4);
              box-shadow:0 1px 0 rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-dialog-header .bp3-icon-large,
      .bp3-dark .bp3-dialog-header .bp3-icon{
        color:#a7b6c2; }

  .bp3-dialog-body{
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto;
    line-height:18px;
    margin:20px; }

  .bp3-dialog-footer{
    -webkit-box-flex:0;
        -ms-flex:0 0 auto;
            flex:0 0 auto;
    margin:0 20px; }

  .bp3-dialog-footer-actions{
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    -webkit-box-pack:end;
        -ms-flex-pack:end;
            justify-content:flex-end; }
    .bp3-dialog-footer-actions .bp3-button{
      margin-left:10px; }
  .bp3-drawer{
    background:#ffffff;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 4px 8px rgba(16, 22, 26, 0.2), 0 18px 46px 6px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 4px 8px rgba(16, 22, 26, 0.2), 0 18px 46px 6px rgba(16, 22, 26, 0.2);
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    -webkit-box-orient:vertical;
    -webkit-box-direction:normal;
        -ms-flex-direction:column;
            flex-direction:column;
    margin:0;
    padding:0; }
    .bp3-drawer:focus{
      outline:0; }
    .bp3-drawer.bp3-position-top{
      height:50%;
      left:0;
      right:0;
      top:0; }
      .bp3-drawer.bp3-position-top.bp3-overlay-enter, .bp3-drawer.bp3-position-top.bp3-overlay-appear{
        -webkit-transform:translateY(-100%);
                transform:translateY(-100%); }
      .bp3-drawer.bp3-position-top.bp3-overlay-enter-active, .bp3-drawer.bp3-position-top.bp3-overlay-appear-active{
        -webkit-transform:translateY(0);
                transform:translateY(0);
        -webkit-transition-delay:0;
                transition-delay:0;
        -webkit-transition-duration:200ms;
                transition-duration:200ms;
        -webkit-transition-property:-webkit-transform;
        transition-property:-webkit-transform;
        transition-property:transform;
        transition-property:transform, -webkit-transform;
        -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
                transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
      .bp3-drawer.bp3-position-top.bp3-overlay-exit{
        -webkit-transform:translateY(0);
                transform:translateY(0); }
      .bp3-drawer.bp3-position-top.bp3-overlay-exit-active{
        -webkit-transform:translateY(-100%);
                transform:translateY(-100%);
        -webkit-transition-delay:0;
                transition-delay:0;
        -webkit-transition-duration:100ms;
                transition-duration:100ms;
        -webkit-transition-property:-webkit-transform;
        transition-property:-webkit-transform;
        transition-property:transform;
        transition-property:transform, -webkit-transform;
        -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
                transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-drawer.bp3-position-bottom{
      bottom:0;
      height:50%;
      left:0;
      right:0; }
      .bp3-drawer.bp3-position-bottom.bp3-overlay-enter, .bp3-drawer.bp3-position-bottom.bp3-overlay-appear{
        -webkit-transform:translateY(100%);
                transform:translateY(100%); }
      .bp3-drawer.bp3-position-bottom.bp3-overlay-enter-active, .bp3-drawer.bp3-position-bottom.bp3-overlay-appear-active{
        -webkit-transform:translateY(0);
                transform:translateY(0);
        -webkit-transition-delay:0;
                transition-delay:0;
        -webkit-transition-duration:200ms;
                transition-duration:200ms;
        -webkit-transition-property:-webkit-transform;
        transition-property:-webkit-transform;
        transition-property:transform;
        transition-property:transform, -webkit-transform;
        -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
                transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
      .bp3-drawer.bp3-position-bottom.bp3-overlay-exit{
        -webkit-transform:translateY(0);
                transform:translateY(0); }
      .bp3-drawer.bp3-position-bottom.bp3-overlay-exit-active{
        -webkit-transform:translateY(100%);
                transform:translateY(100%);
        -webkit-transition-delay:0;
                transition-delay:0;
        -webkit-transition-duration:100ms;
                transition-duration:100ms;
        -webkit-transition-property:-webkit-transform;
        transition-property:-webkit-transform;
        transition-property:transform;
        transition-property:transform, -webkit-transform;
        -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
                transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-drawer.bp3-position-left{
      bottom:0;
      left:0;
      top:0;
      width:50%; }
      .bp3-drawer.bp3-position-left.bp3-overlay-enter, .bp3-drawer.bp3-position-left.bp3-overlay-appear{
        -webkit-transform:translateX(-100%);
                transform:translateX(-100%); }
      .bp3-drawer.bp3-position-left.bp3-overlay-enter-active, .bp3-drawer.bp3-position-left.bp3-overlay-appear-active{
        -webkit-transform:translateX(0);
                transform:translateX(0);
        -webkit-transition-delay:0;
                transition-delay:0;
        -webkit-transition-duration:200ms;
                transition-duration:200ms;
        -webkit-transition-property:-webkit-transform;
        transition-property:-webkit-transform;
        transition-property:transform;
        transition-property:transform, -webkit-transform;
        -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
                transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
      .bp3-drawer.bp3-position-left.bp3-overlay-exit{
        -webkit-transform:translateX(0);
                transform:translateX(0); }
      .bp3-drawer.bp3-position-left.bp3-overlay-exit-active{
        -webkit-transform:translateX(-100%);
                transform:translateX(-100%);
        -webkit-transition-delay:0;
                transition-delay:0;
        -webkit-transition-duration:100ms;
                transition-duration:100ms;
        -webkit-transition-property:-webkit-transform;
        transition-property:-webkit-transform;
        transition-property:transform;
        transition-property:transform, -webkit-transform;
        -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
                transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-drawer.bp3-position-right{
      bottom:0;
      right:0;
      top:0;
      width:50%; }
      .bp3-drawer.bp3-position-right.bp3-overlay-enter, .bp3-drawer.bp3-position-right.bp3-overlay-appear{
        -webkit-transform:translateX(100%);
                transform:translateX(100%); }
      .bp3-drawer.bp3-position-right.bp3-overlay-enter-active, .bp3-drawer.bp3-position-right.bp3-overlay-appear-active{
        -webkit-transform:translateX(0);
                transform:translateX(0);
        -webkit-transition-delay:0;
                transition-delay:0;
        -webkit-transition-duration:200ms;
                transition-duration:200ms;
        -webkit-transition-property:-webkit-transform;
        transition-property:-webkit-transform;
        transition-property:transform;
        transition-property:transform, -webkit-transform;
        -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
                transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
      .bp3-drawer.bp3-position-right.bp3-overlay-exit{
        -webkit-transform:translateX(0);
                transform:translateX(0); }
      .bp3-drawer.bp3-position-right.bp3-overlay-exit-active{
        -webkit-transform:translateX(100%);
                transform:translateX(100%);
        -webkit-transition-delay:0;
                transition-delay:0;
        -webkit-transition-duration:100ms;
                transition-duration:100ms;
        -webkit-transition-property:-webkit-transform;
        transition-property:-webkit-transform;
        transition-property:transform;
        transition-property:transform, -webkit-transform;
        -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
                transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right):not(.bp3-vertical){
      bottom:0;
      right:0;
      top:0;
      width:50%; }
      .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
      .bp3-position-right):not(.bp3-vertical).bp3-overlay-enter, .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
      .bp3-position-right):not(.bp3-vertical).bp3-overlay-appear{
        -webkit-transform:translateX(100%);
                transform:translateX(100%); }
      .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
      .bp3-position-right):not(.bp3-vertical).bp3-overlay-enter-active, .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
      .bp3-position-right):not(.bp3-vertical).bp3-overlay-appear-active{
        -webkit-transform:translateX(0);
                transform:translateX(0);
        -webkit-transition-delay:0;
                transition-delay:0;
        -webkit-transition-duration:200ms;
                transition-duration:200ms;
        -webkit-transition-property:-webkit-transform;
        transition-property:-webkit-transform;
        transition-property:transform;
        transition-property:transform, -webkit-transform;
        -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
                transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
      .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
      .bp3-position-right):not(.bp3-vertical).bp3-overlay-exit{
        -webkit-transform:translateX(0);
                transform:translateX(0); }
      .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
      .bp3-position-right):not(.bp3-vertical).bp3-overlay-exit-active{
        -webkit-transform:translateX(100%);
                transform:translateX(100%);
        -webkit-transition-delay:0;
                transition-delay:0;
        -webkit-transition-duration:100ms;
                transition-duration:100ms;
        -webkit-transition-property:-webkit-transform;
        transition-property:-webkit-transform;
        transition-property:transform;
        transition-property:transform, -webkit-transform;
        -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
                transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right).bp3-vertical{
      bottom:0;
      height:50%;
      left:0;
      right:0; }
      .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
      .bp3-position-right).bp3-vertical.bp3-overlay-enter, .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
      .bp3-position-right).bp3-vertical.bp3-overlay-appear{
        -webkit-transform:translateY(100%);
                transform:translateY(100%); }
      .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
      .bp3-position-right).bp3-vertical.bp3-overlay-enter-active, .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
      .bp3-position-right).bp3-vertical.bp3-overlay-appear-active{
        -webkit-transform:translateY(0);
                transform:translateY(0);
        -webkit-transition-delay:0;
                transition-delay:0;
        -webkit-transition-duration:200ms;
                transition-duration:200ms;
        -webkit-transition-property:-webkit-transform;
        transition-property:-webkit-transform;
        transition-property:transform;
        transition-property:transform, -webkit-transform;
        -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
                transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
      .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
      .bp3-position-right).bp3-vertical.bp3-overlay-exit{
        -webkit-transform:translateY(0);
                transform:translateY(0); }
      .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
      .bp3-position-right).bp3-vertical.bp3-overlay-exit-active{
        -webkit-transform:translateY(100%);
                transform:translateY(100%);
        -webkit-transition-delay:0;
                transition-delay:0;
        -webkit-transition-duration:100ms;
                transition-duration:100ms;
        -webkit-transition-property:-webkit-transform;
        transition-property:-webkit-transform;
        transition-property:transform;
        transition-property:transform, -webkit-transform;
        -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
                transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-drawer.bp3-dark,
    .bp3-dark .bp3-drawer{
      background:#30404d;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 4px 8px rgba(16, 22, 26, 0.4), 0 18px 46px 6px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 4px 8px rgba(16, 22, 26, 0.4), 0 18px 46px 6px rgba(16, 22, 26, 0.4);
      color:#f5f8fa; }

  .bp3-drawer-header{
    -webkit-box-align:center;
        -ms-flex-align:center;
            align-items:center;
    border-radius:0;
    -webkit-box-shadow:0 1px 0 rgba(16, 22, 26, 0.15);
            box-shadow:0 1px 0 rgba(16, 22, 26, 0.15);
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    -webkit-box-flex:0;
        -ms-flex:0 0 auto;
            flex:0 0 auto;
    min-height:40px;
    padding:5px;
    padding-left:20px;
    position:relative; }
    .bp3-drawer-header .bp3-icon-large,
    .bp3-drawer-header .bp3-icon{
      color:#5c7080;
      -webkit-box-flex:0;
          -ms-flex:0 0 auto;
              flex:0 0 auto;
      margin-right:10px; }
    .bp3-drawer-header .bp3-heading{
      overflow:hidden;
      text-overflow:ellipsis;
      white-space:nowrap;
      word-wrap:normal;
      -webkit-box-flex:1;
          -ms-flex:1 1 auto;
              flex:1 1 auto;
      line-height:inherit;
      margin:0; }
      .bp3-drawer-header .bp3-heading:last-child{
        margin-right:20px; }
    .bp3-dark .bp3-drawer-header{
      -webkit-box-shadow:0 1px 0 rgba(16, 22, 26, 0.4);
              box-shadow:0 1px 0 rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-drawer-header .bp3-icon-large,
      .bp3-dark .bp3-drawer-header .bp3-icon{
        color:#a7b6c2; }

  .bp3-drawer-body{
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto;
    line-height:18px;
    overflow:auto; }

  .bp3-drawer-footer{
    -webkit-box-shadow:inset 0 1px 0 rgba(16, 22, 26, 0.15);
            box-shadow:inset 0 1px 0 rgba(16, 22, 26, 0.15);
    -webkit-box-flex:0;
        -ms-flex:0 0 auto;
            flex:0 0 auto;
    padding:10px 20px;
    position:relative; }
    .bp3-dark .bp3-drawer-footer{
      -webkit-box-shadow:inset 0 1px 0 rgba(16, 22, 26, 0.4);
              box-shadow:inset 0 1px 0 rgba(16, 22, 26, 0.4); }
  .bp3-editable-text{
    cursor:text;
    display:inline-block;
    max-width:100%;
    position:relative;
    vertical-align:top;
    white-space:nowrap; }
    .bp3-editable-text::before{
      bottom:-3px;
      left:-3px;
      position:absolute;
      right:-3px;
      top:-3px;
      border-radius:3px;
      content:"";
      -webkit-transition:background-color 100ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
      transition:background-color 100ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
      transition:background-color 100ms cubic-bezier(0.4, 1, 0.75, 0.9), box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
      transition:background-color 100ms cubic-bezier(0.4, 1, 0.75, 0.9), box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-editable-text:hover::before{
      -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.15);
              box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.15); }
    .bp3-editable-text.bp3-editable-text-editing::before{
      background-color:#ffffff;
      -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-editable-text.bp3-disabled::before{
      -webkit-box-shadow:none;
              box-shadow:none; }
    .bp3-editable-text.bp3-intent-primary .bp3-editable-text-input,
    .bp3-editable-text.bp3-intent-primary .bp3-editable-text-content{
      color:#137cbd; }
    .bp3-editable-text.bp3-intent-primary:hover::before{
      -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(19, 124, 189, 0.4);
              box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(19, 124, 189, 0.4); }
    .bp3-editable-text.bp3-intent-primary.bp3-editable-text-editing::before{
      -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-editable-text.bp3-intent-success .bp3-editable-text-input,
    .bp3-editable-text.bp3-intent-success .bp3-editable-text-content{
      color:#0f9960; }
    .bp3-editable-text.bp3-intent-success:hover::before{
      -webkit-box-shadow:0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), inset 0 0 0 1px rgba(15, 153, 96, 0.4);
              box-shadow:0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), inset 0 0 0 1px rgba(15, 153, 96, 0.4); }
    .bp3-editable-text.bp3-intent-success.bp3-editable-text-editing::before{
      -webkit-box-shadow:0 0 0 1px #0f9960, 0 0 0 3px rgba(15, 153, 96, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #0f9960, 0 0 0 3px rgba(15, 153, 96, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-editable-text.bp3-intent-warning .bp3-editable-text-input,
    .bp3-editable-text.bp3-intent-warning .bp3-editable-text-content{
      color:#d9822b; }
    .bp3-editable-text.bp3-intent-warning:hover::before{
      -webkit-box-shadow:0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), inset 0 0 0 1px rgba(217, 130, 43, 0.4);
              box-shadow:0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), inset 0 0 0 1px rgba(217, 130, 43, 0.4); }
    .bp3-editable-text.bp3-intent-warning.bp3-editable-text-editing::before{
      -webkit-box-shadow:0 0 0 1px #d9822b, 0 0 0 3px rgba(217, 130, 43, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #d9822b, 0 0 0 3px rgba(217, 130, 43, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-editable-text.bp3-intent-danger .bp3-editable-text-input,
    .bp3-editable-text.bp3-intent-danger .bp3-editable-text-content{
      color:#db3737; }
    .bp3-editable-text.bp3-intent-danger:hover::before{
      -webkit-box-shadow:0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), inset 0 0 0 1px rgba(219, 55, 55, 0.4);
              box-shadow:0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), inset 0 0 0 1px rgba(219, 55, 55, 0.4); }
    .bp3-editable-text.bp3-intent-danger.bp3-editable-text-editing::before{
      -webkit-box-shadow:0 0 0 1px #db3737, 0 0 0 3px rgba(219, 55, 55, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #db3737, 0 0 0 3px rgba(219, 55, 55, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-dark .bp3-editable-text:hover::before{
      -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(255, 255, 255, 0.15);
              box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(255, 255, 255, 0.15); }
    .bp3-dark .bp3-editable-text.bp3-editable-text-editing::before{
      background-color:rgba(16, 22, 26, 0.3);
      -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-editable-text.bp3-disabled::before{
      -webkit-box-shadow:none;
              box-shadow:none; }
    .bp3-dark .bp3-editable-text.bp3-intent-primary .bp3-editable-text-content{
      color:#48aff0; }
    .bp3-dark .bp3-editable-text.bp3-intent-primary:hover::before{
      -webkit-box-shadow:0 0 0 0 rgba(72, 175, 240, 0), 0 0 0 0 rgba(72, 175, 240, 0), inset 0 0 0 1px rgba(72, 175, 240, 0.4);
              box-shadow:0 0 0 0 rgba(72, 175, 240, 0), 0 0 0 0 rgba(72, 175, 240, 0), inset 0 0 0 1px rgba(72, 175, 240, 0.4); }
    .bp3-dark .bp3-editable-text.bp3-intent-primary.bp3-editable-text-editing::before{
      -webkit-box-shadow:0 0 0 1px #48aff0, 0 0 0 3px rgba(72, 175, 240, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px #48aff0, 0 0 0 3px rgba(72, 175, 240, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-editable-text.bp3-intent-success .bp3-editable-text-content{
      color:#3dcc91; }
    .bp3-dark .bp3-editable-text.bp3-intent-success:hover::before{
      -webkit-box-shadow:0 0 0 0 rgba(61, 204, 145, 0), 0 0 0 0 rgba(61, 204, 145, 0), inset 0 0 0 1px rgba(61, 204, 145, 0.4);
              box-shadow:0 0 0 0 rgba(61, 204, 145, 0), 0 0 0 0 rgba(61, 204, 145, 0), inset 0 0 0 1px rgba(61, 204, 145, 0.4); }
    .bp3-dark .bp3-editable-text.bp3-intent-success.bp3-editable-text-editing::before{
      -webkit-box-shadow:0 0 0 1px #3dcc91, 0 0 0 3px rgba(61, 204, 145, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px #3dcc91, 0 0 0 3px rgba(61, 204, 145, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-editable-text.bp3-intent-warning .bp3-editable-text-content{
      color:#ffb366; }
    .bp3-dark .bp3-editable-text.bp3-intent-warning:hover::before{
      -webkit-box-shadow:0 0 0 0 rgba(255, 179, 102, 0), 0 0 0 0 rgba(255, 179, 102, 0), inset 0 0 0 1px rgba(255, 179, 102, 0.4);
              box-shadow:0 0 0 0 rgba(255, 179, 102, 0), 0 0 0 0 rgba(255, 179, 102, 0), inset 0 0 0 1px rgba(255, 179, 102, 0.4); }
    .bp3-dark .bp3-editable-text.bp3-intent-warning.bp3-editable-text-editing::before{
      -webkit-box-shadow:0 0 0 1px #ffb366, 0 0 0 3px rgba(255, 179, 102, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px #ffb366, 0 0 0 3px rgba(255, 179, 102, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-editable-text.bp3-intent-danger .bp3-editable-text-content{
      color:#ff7373; }
    .bp3-dark .bp3-editable-text.bp3-intent-danger:hover::before{
      -webkit-box-shadow:0 0 0 0 rgba(255, 115, 115, 0), 0 0 0 0 rgba(255, 115, 115, 0), inset 0 0 0 1px rgba(255, 115, 115, 0.4);
              box-shadow:0 0 0 0 rgba(255, 115, 115, 0), 0 0 0 0 rgba(255, 115, 115, 0), inset 0 0 0 1px rgba(255, 115, 115, 0.4); }
    .bp3-dark .bp3-editable-text.bp3-intent-danger.bp3-editable-text-editing::before{
      -webkit-box-shadow:0 0 0 1px #ff7373, 0 0 0 3px rgba(255, 115, 115, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px #ff7373, 0 0 0 3px rgba(255, 115, 115, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }

  .bp3-editable-text-input,
  .bp3-editable-text-content{
    color:inherit;
    display:inherit;
    font:inherit;
    letter-spacing:inherit;
    max-width:inherit;
    min-width:inherit;
    position:relative;
    resize:none;
    text-transform:inherit;
    vertical-align:top; }

  .bp3-editable-text-input{
    background:none;
    border:none;
    -webkit-box-shadow:none;
            box-shadow:none;
    padding:0;
    white-space:pre-wrap;
    width:100%; }
    .bp3-editable-text-input::-webkit-input-placeholder{
      color:rgba(92, 112, 128, 0.6);
      opacity:1; }
    .bp3-editable-text-input::-moz-placeholder{
      color:rgba(92, 112, 128, 0.6);
      opacity:1; }
    .bp3-editable-text-input:-ms-input-placeholder{
      color:rgba(92, 112, 128, 0.6);
      opacity:1; }
    .bp3-editable-text-input::-ms-input-placeholder{
      color:rgba(92, 112, 128, 0.6);
      opacity:1; }
    .bp3-editable-text-input::placeholder{
      color:rgba(92, 112, 128, 0.6);
      opacity:1; }
    .bp3-editable-text-input:focus{
      outline:none; }
    .bp3-editable-text-input::-ms-clear{
      display:none; }

  .bp3-editable-text-content{
    overflow:hidden;
    padding-right:2px;
    text-overflow:ellipsis;
    white-space:pre; }
    .bp3-editable-text-editing > .bp3-editable-text-content{
      left:0;
      position:absolute;
      visibility:hidden; }
    .bp3-editable-text-placeholder > .bp3-editable-text-content{
      color:rgba(92, 112, 128, 0.6); }
      .bp3-dark .bp3-editable-text-placeholder > .bp3-editable-text-content{
        color:rgba(167, 182, 194, 0.6); }

  .bp3-editable-text.bp3-multiline{
    display:block; }
    .bp3-editable-text.bp3-multiline .bp3-editable-text-content{
      overflow:auto;
      white-space:pre-wrap;
      word-wrap:break-word; }
  .bp3-divider{
    border-bottom:1px solid rgba(16, 22, 26, 0.15);
    border-right:1px solid rgba(16, 22, 26, 0.15);
    margin:5px; }
    .bp3-dark .bp3-divider{
      border-color:rgba(16, 22, 26, 0.4); }
  .bp3-control-group{
    -webkit-transform:translateZ(0);
            transform:translateZ(0);
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    -webkit-box-orient:horizontal;
    -webkit-box-direction:normal;
        -ms-flex-direction:row;
            flex-direction:row;
    -webkit-box-align:stretch;
        -ms-flex-align:stretch;
            align-items:stretch; }
    .bp3-control-group > *{
      -webkit-box-flex:0;
          -ms-flex-positive:0;
              flex-grow:0;
      -ms-flex-negative:0;
          flex-shrink:0; }
    .bp3-control-group > .bp3-fill{
      -webkit-box-flex:1;
          -ms-flex-positive:1;
              flex-grow:1;
      -ms-flex-negative:1;
          flex-shrink:1; }
    .bp3-control-group .bp3-button,
    .bp3-control-group .bp3-html-select,
    .bp3-control-group .bp3-input,
    .bp3-control-group .bp3-select{
      position:relative; }
    .bp3-control-group .bp3-input{
      border-radius:inherit;
      z-index:2; }
      .bp3-control-group .bp3-input:focus{
        border-radius:3px;
        z-index:14; }
      .bp3-control-group .bp3-input[class*="bp3-intent"]{
        z-index:13; }
        .bp3-control-group .bp3-input[class*="bp3-intent"]:focus{
          z-index:15; }
      .bp3-control-group .bp3-input[readonly], .bp3-control-group .bp3-input:disabled, .bp3-control-group .bp3-input.bp3-disabled{
        z-index:1; }
    .bp3-control-group .bp3-input-group[class*="bp3-intent"] .bp3-input{
      z-index:13; }
      .bp3-control-group .bp3-input-group[class*="bp3-intent"] .bp3-input:focus{
        z-index:15; }
    .bp3-control-group .bp3-button,
    .bp3-control-group .bp3-html-select select,
    .bp3-control-group .bp3-select select{
      -webkit-transform:translateZ(0);
              transform:translateZ(0);
      border-radius:inherit;
      z-index:4; }
      .bp3-control-group .bp3-button:focus,
      .bp3-control-group .bp3-html-select select:focus,
      .bp3-control-group .bp3-select select:focus{
        z-index:5; }
      .bp3-control-group .bp3-button:hover,
      .bp3-control-group .bp3-html-select select:hover,
      .bp3-control-group .bp3-select select:hover{
        z-index:6; }
      .bp3-control-group .bp3-button:active,
      .bp3-control-group .bp3-html-select select:active,
      .bp3-control-group .bp3-select select:active{
        z-index:7; }
      .bp3-control-group .bp3-button[readonly], .bp3-control-group .bp3-button:disabled, .bp3-control-group .bp3-button.bp3-disabled,
      .bp3-control-group .bp3-html-select select[readonly],
      .bp3-control-group .bp3-html-select select:disabled,
      .bp3-control-group .bp3-html-select select.bp3-disabled,
      .bp3-control-group .bp3-select select[readonly],
      .bp3-control-group .bp3-select select:disabled,
      .bp3-control-group .bp3-select select.bp3-disabled{
        z-index:3; }
      .bp3-control-group .bp3-button[class*="bp3-intent"],
      .bp3-control-group .bp3-html-select select[class*="bp3-intent"],
      .bp3-control-group .bp3-select select[class*="bp3-intent"]{
        z-index:9; }
        .bp3-control-group .bp3-button[class*="bp3-intent"]:focus,
        .bp3-control-group .bp3-html-select select[class*="bp3-intent"]:focus,
        .bp3-control-group .bp3-select select[class*="bp3-intent"]:focus{
          z-index:10; }
        .bp3-control-group .bp3-button[class*="bp3-intent"]:hover,
        .bp3-control-group .bp3-html-select select[class*="bp3-intent"]:hover,
        .bp3-control-group .bp3-select select[class*="bp3-intent"]:hover{
          z-index:11; }
        .bp3-control-group .bp3-button[class*="bp3-intent"]:active,
        .bp3-control-group .bp3-html-select select[class*="bp3-intent"]:active,
        .bp3-control-group .bp3-select select[class*="bp3-intent"]:active{
          z-index:12; }
        .bp3-control-group .bp3-button[class*="bp3-intent"][readonly], .bp3-control-group .bp3-button[class*="bp3-intent"]:disabled, .bp3-control-group .bp3-button[class*="bp3-intent"].bp3-disabled,
        .bp3-control-group .bp3-html-select select[class*="bp3-intent"][readonly],
        .bp3-control-group .bp3-html-select select[class*="bp3-intent"]:disabled,
        .bp3-control-group .bp3-html-select select[class*="bp3-intent"].bp3-disabled,
        .bp3-control-group .bp3-select select[class*="bp3-intent"][readonly],
        .bp3-control-group .bp3-select select[class*="bp3-intent"]:disabled,
        .bp3-control-group .bp3-select select[class*="bp3-intent"].bp3-disabled{
          z-index:8; }
    .bp3-control-group .bp3-input-group > .bp3-icon,
    .bp3-control-group .bp3-input-group > .bp3-button,
    .bp3-control-group .bp3-input-group > .bp3-input-action{
      z-index:16; }
    .bp3-control-group .bp3-select::after,
    .bp3-control-group .bp3-html-select::after,
    .bp3-control-group .bp3-select > .bp3-icon,
    .bp3-control-group .bp3-html-select > .bp3-icon{
      z-index:17; }
    .bp3-control-group .bp3-select:focus-within{
      z-index:5; }
    .bp3-control-group:not(.bp3-vertical) > *:not(.bp3-divider){
      margin-right:-1px; }
    .bp3-control-group:not(.bp3-vertical) > .bp3-divider:not(:first-child){
      margin-left:6px; }
    .bp3-dark .bp3-control-group:not(.bp3-vertical) > *:not(.bp3-divider){
      margin-right:0; }
    .bp3-dark .bp3-control-group:not(.bp3-vertical) > .bp3-button + .bp3-button{
      margin-left:1px; }
    .bp3-control-group .bp3-popover-wrapper,
    .bp3-control-group .bp3-popover-target{
      border-radius:inherit; }
    .bp3-control-group > :first-child{
      border-radius:3px 0 0 3px; }
    .bp3-control-group > :last-child{
      border-radius:0 3px 3px 0;
      margin-right:0; }
    .bp3-control-group > :only-child{
      border-radius:3px;
      margin-right:0; }
    .bp3-control-group .bp3-input-group .bp3-button{
      border-radius:3px; }
    .bp3-control-group .bp3-numeric-input:not(:first-child) .bp3-input-group{
      border-bottom-left-radius:0;
      border-top-left-radius:0; }
    .bp3-control-group.bp3-fill{
      width:100%; }
    .bp3-control-group > .bp3-fill{
      -webkit-box-flex:1;
          -ms-flex:1 1 auto;
              flex:1 1 auto; }
    .bp3-control-group.bp3-fill > *:not(.bp3-fixed){
      -webkit-box-flex:1;
          -ms-flex:1 1 auto;
              flex:1 1 auto; }
    .bp3-control-group.bp3-vertical{
      -webkit-box-orient:vertical;
      -webkit-box-direction:normal;
          -ms-flex-direction:column;
              flex-direction:column; }
      .bp3-control-group.bp3-vertical > *{
        margin-top:-1px; }
      .bp3-control-group.bp3-vertical > :first-child{
        border-radius:3px 3px 0 0;
        margin-top:0; }
      .bp3-control-group.bp3-vertical > :last-child{
        border-radius:0 0 3px 3px; }
  .bp3-control{
    cursor:pointer;
    display:block;
    margin-bottom:10px;
    position:relative;
    text-transform:none; }
    .bp3-control input:checked ~ .bp3-control-indicator{
      background-color:#137cbd;
      background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.1)), to(rgba(255, 255, 255, 0)));
      background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0));
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
      color:#ffffff; }
    .bp3-control:hover input:checked ~ .bp3-control-indicator{
      background-color:#106ba3;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2); }
    .bp3-control input:not(:disabled):active:checked ~ .bp3-control-indicator{
      background:#0e5a8a;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
    .bp3-control input:disabled:checked ~ .bp3-control-indicator{
      background:rgba(19, 124, 189, 0.5);
      -webkit-box-shadow:none;
              box-shadow:none; }
    .bp3-dark .bp3-control input:checked ~ .bp3-control-indicator{
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-control:hover input:checked ~ .bp3-control-indicator{
      background-color:#106ba3;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-control input:not(:disabled):active:checked ~ .bp3-control-indicator{
      background-color:#0e5a8a;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
    .bp3-dark .bp3-control input:disabled:checked ~ .bp3-control-indicator{
      background:rgba(14, 90, 138, 0.5);
      -webkit-box-shadow:none;
              box-shadow:none; }
    .bp3-control:not(.bp3-align-right){
      padding-left:26px; }
      .bp3-control:not(.bp3-align-right) .bp3-control-indicator{
        margin-left:-26px; }
    .bp3-control.bp3-align-right{
      padding-right:26px; }
      .bp3-control.bp3-align-right .bp3-control-indicator{
        margin-right:-26px; }
    .bp3-control.bp3-disabled{
      color:rgba(92, 112, 128, 0.6);
      cursor:not-allowed; }
    .bp3-control.bp3-inline{
      display:inline-block;
      margin-right:20px; }
    .bp3-control input{
      left:0;
      opacity:0;
      position:absolute;
      top:0;
      z-index:-1; }
    .bp3-control .bp3-control-indicator{
      background-clip:padding-box;
      background-color:#f5f8fa;
      background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.8)), to(rgba(255, 255, 255, 0)));
      background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.8), rgba(255, 255, 255, 0));
      border:none;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
      cursor:pointer;
      display:inline-block;
      font-size:16px;
      height:1em;
      margin-right:10px;
      margin-top:-3px;
      position:relative;
      -webkit-user-select:none;
        -moz-user-select:none;
          -ms-user-select:none;
              user-select:none;
      vertical-align:middle;
      width:1em; }
      .bp3-control .bp3-control-indicator::before{
        content:"";
        display:block;
        height:1em;
        width:1em; }
    .bp3-control:hover .bp3-control-indicator{
      background-color:#ebf1f5; }
    .bp3-control input:not(:disabled):active ~ .bp3-control-indicator{
      background:#d8e1e8;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
    .bp3-control input:disabled ~ .bp3-control-indicator{
      background:rgba(206, 217, 224, 0.5);
      -webkit-box-shadow:none;
              box-shadow:none;
      cursor:not-allowed; }
    .bp3-control input:focus ~ .bp3-control-indicator{
      outline:rgba(19, 124, 189, 0.6) auto 2px;
      outline-offset:2px;
      -moz-outline-radius:6px; }
    .bp3-control.bp3-align-right .bp3-control-indicator{
      float:right;
      margin-left:10px;
      margin-top:1px; }
    .bp3-control.bp3-large{
      font-size:16px; }
      .bp3-control.bp3-large:not(.bp3-align-right){
        padding-left:30px; }
        .bp3-control.bp3-large:not(.bp3-align-right) .bp3-control-indicator{
          margin-left:-30px; }
      .bp3-control.bp3-large.bp3-align-right{
        padding-right:30px; }
        .bp3-control.bp3-large.bp3-align-right .bp3-control-indicator{
          margin-right:-30px; }
      .bp3-control.bp3-large .bp3-control-indicator{
        font-size:20px; }
      .bp3-control.bp3-large.bp3-align-right .bp3-control-indicator{
        margin-top:0; }
    .bp3-control.bp3-checkbox input:indeterminate ~ .bp3-control-indicator{
      background-color:#137cbd;
      background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.1)), to(rgba(255, 255, 255, 0)));
      background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0));
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
      color:#ffffff; }
    .bp3-control.bp3-checkbox:hover input:indeterminate ~ .bp3-control-indicator{
      background-color:#106ba3;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2); }
    .bp3-control.bp3-checkbox input:not(:disabled):active:indeterminate ~ .bp3-control-indicator{
      background:#0e5a8a;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
    .bp3-control.bp3-checkbox input:disabled:indeterminate ~ .bp3-control-indicator{
      background:rgba(19, 124, 189, 0.5);
      -webkit-box-shadow:none;
              box-shadow:none; }
    .bp3-dark .bp3-control.bp3-checkbox input:indeterminate ~ .bp3-control-indicator{
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-control.bp3-checkbox:hover input:indeterminate ~ .bp3-control-indicator{
      background-color:#106ba3;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-control.bp3-checkbox input:not(:disabled):active:indeterminate ~ .bp3-control-indicator{
      background-color:#0e5a8a;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
    .bp3-dark .bp3-control.bp3-checkbox input:disabled:indeterminate ~ .bp3-control-indicator{
      background:rgba(14, 90, 138, 0.5);
      -webkit-box-shadow:none;
              box-shadow:none; }
    .bp3-control.bp3-checkbox .bp3-control-indicator{
      border-radius:3px; }
    .bp3-control.bp3-checkbox input:checked ~ .bp3-control-indicator::before{
      background-image:url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 16 16'%3e%3cpath fill-rule='evenodd' clip-rule='evenodd' d='M12 5c-.28 0-.53.11-.71.29L7 9.59l-2.29-2.3a1.003 1.003 0 00-1.42 1.42l3 3c.18.18.43.29.71.29s.53-.11.71-.29l5-5A1.003 1.003 0 0012 5z' fill='white'/%3e%3c/svg%3e"); }
    .bp3-control.bp3-checkbox input:indeterminate ~ .bp3-control-indicator::before{
      background-image:url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 16 16'%3e%3cpath fill-rule='evenodd' clip-rule='evenodd' d='M11 7H5c-.55 0-1 .45-1 1s.45 1 1 1h6c.55 0 1-.45 1-1s-.45-1-1-1z' fill='white'/%3e%3c/svg%3e"); }
    .bp3-control.bp3-radio .bp3-control-indicator{
      border-radius:50%; }
    .bp3-control.bp3-radio input:checked ~ .bp3-control-indicator::before{
      background-image:radial-gradient(#ffffff, #ffffff 28%, transparent 32%); }
    .bp3-control.bp3-radio input:checked:disabled ~ .bp3-control-indicator::before{
      opacity:0.5; }
    .bp3-control.bp3-radio input:focus ~ .bp3-control-indicator{
      -moz-outline-radius:16px; }
    .bp3-control.bp3-switch input ~ .bp3-control-indicator{
      background:rgba(167, 182, 194, 0.5); }
    .bp3-control.bp3-switch:hover input ~ .bp3-control-indicator{
      background:rgba(115, 134, 148, 0.5); }
    .bp3-control.bp3-switch input:not(:disabled):active ~ .bp3-control-indicator{
      background:rgba(92, 112, 128, 0.5); }
    .bp3-control.bp3-switch input:disabled ~ .bp3-control-indicator{
      background:rgba(206, 217, 224, 0.5); }
      .bp3-control.bp3-switch input:disabled ~ .bp3-control-indicator::before{
        background:rgba(255, 255, 255, 0.8); }
    .bp3-control.bp3-switch input:checked ~ .bp3-control-indicator{
      background:#137cbd; }
    .bp3-control.bp3-switch:hover input:checked ~ .bp3-control-indicator{
      background:#106ba3; }
    .bp3-control.bp3-switch input:checked:not(:disabled):active ~ .bp3-control-indicator{
      background:#0e5a8a; }
    .bp3-control.bp3-switch input:checked:disabled ~ .bp3-control-indicator{
      background:rgba(19, 124, 189, 0.5); }
      .bp3-control.bp3-switch input:checked:disabled ~ .bp3-control-indicator::before{
        background:rgba(255, 255, 255, 0.8); }
    .bp3-control.bp3-switch:not(.bp3-align-right){
      padding-left:38px; }
      .bp3-control.bp3-switch:not(.bp3-align-right) .bp3-control-indicator{
        margin-left:-38px; }
    .bp3-control.bp3-switch.bp3-align-right{
      padding-right:38px; }
      .bp3-control.bp3-switch.bp3-align-right .bp3-control-indicator{
        margin-right:-38px; }
    .bp3-control.bp3-switch .bp3-control-indicator{
      border:none;
      border-radius:1.75em;
      -webkit-box-shadow:none !important;
              box-shadow:none !important;
      min-width:1.75em;
      -webkit-transition:background-color 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
      transition:background-color 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
      width:auto; }
      .bp3-control.bp3-switch .bp3-control-indicator::before{
        background:#ffffff;
        border-radius:50%;
        -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 1px 1px rgba(16, 22, 26, 0.2);
                box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 1px 1px rgba(16, 22, 26, 0.2);
        height:calc(1em - 4px);
        left:0;
        margin:2px;
        position:absolute;
        -webkit-transition:left 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
        transition:left 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
        width:calc(1em - 4px); }
    .bp3-control.bp3-switch input:checked ~ .bp3-control-indicator::before{
      left:calc(100% - 1em); }
    .bp3-control.bp3-switch.bp3-large:not(.bp3-align-right){
      padding-left:45px; }
      .bp3-control.bp3-switch.bp3-large:not(.bp3-align-right) .bp3-control-indicator{
        margin-left:-45px; }
    .bp3-control.bp3-switch.bp3-large.bp3-align-right{
      padding-right:45px; }
      .bp3-control.bp3-switch.bp3-large.bp3-align-right .bp3-control-indicator{
        margin-right:-45px; }
    .bp3-dark .bp3-control.bp3-switch input ~ .bp3-control-indicator{
      background:rgba(16, 22, 26, 0.5); }
    .bp3-dark .bp3-control.bp3-switch:hover input ~ .bp3-control-indicator{
      background:rgba(16, 22, 26, 0.7); }
    .bp3-dark .bp3-control.bp3-switch input:not(:disabled):active ~ .bp3-control-indicator{
      background:rgba(16, 22, 26, 0.9); }
    .bp3-dark .bp3-control.bp3-switch input:disabled ~ .bp3-control-indicator{
      background:rgba(57, 75, 89, 0.5); }
      .bp3-dark .bp3-control.bp3-switch input:disabled ~ .bp3-control-indicator::before{
        background:rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-control.bp3-switch input:checked ~ .bp3-control-indicator{
      background:#137cbd; }
    .bp3-dark .bp3-control.bp3-switch:hover input:checked ~ .bp3-control-indicator{
      background:#106ba3; }
    .bp3-dark .bp3-control.bp3-switch input:checked:not(:disabled):active ~ .bp3-control-indicator{
      background:#0e5a8a; }
    .bp3-dark .bp3-control.bp3-switch input:checked:disabled ~ .bp3-control-indicator{
      background:rgba(14, 90, 138, 0.5); }
      .bp3-dark .bp3-control.bp3-switch input:checked:disabled ~ .bp3-control-indicator::before{
        background:rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-control.bp3-switch .bp3-control-indicator::before{
      background:#394b59;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-control.bp3-switch input:checked ~ .bp3-control-indicator::before{
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4); }
    .bp3-control.bp3-switch .bp3-switch-inner-text{
      font-size:0.7em;
      text-align:center; }
    .bp3-control.bp3-switch .bp3-control-indicator-child:first-child{
      line-height:0;
      margin-left:0.5em;
      margin-right:1.2em;
      visibility:hidden; }
    .bp3-control.bp3-switch .bp3-control-indicator-child:last-child{
      line-height:1em;
      margin-left:1.2em;
      margin-right:0.5em;
      visibility:visible; }
    .bp3-control.bp3-switch input:checked ~ .bp3-control-indicator .bp3-control-indicator-child:first-child{
      line-height:1em;
      visibility:visible; }
    .bp3-control.bp3-switch input:checked ~ .bp3-control-indicator .bp3-control-indicator-child:last-child{
      line-height:0;
      visibility:hidden; }
    .bp3-dark .bp3-control{
      color:#f5f8fa; }
      .bp3-dark .bp3-control.bp3-disabled{
        color:rgba(167, 182, 194, 0.6); }
      .bp3-dark .bp3-control .bp3-control-indicator{
        background-color:#394b59;
        background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.05)), to(rgba(255, 255, 255, 0)));
        background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.05), rgba(255, 255, 255, 0));
        -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
                box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-control:hover .bp3-control-indicator{
        background-color:#30404d; }
      .bp3-dark .bp3-control input:not(:disabled):active ~ .bp3-control-indicator{
        background:#202b33;
        -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2);
                box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
      .bp3-dark .bp3-control input:disabled ~ .bp3-control-indicator{
        background:rgba(57, 75, 89, 0.5);
        -webkit-box-shadow:none;
                box-shadow:none;
        cursor:not-allowed; }
      .bp3-dark .bp3-control.bp3-checkbox input:disabled:checked ~ .bp3-control-indicator, .bp3-dark .bp3-control.bp3-checkbox input:disabled:indeterminate ~ .bp3-control-indicator{
        color:rgba(167, 182, 194, 0.6); }
  .bp3-file-input{
    cursor:pointer;
    display:inline-block;
    height:30px;
    position:relative; }
    .bp3-file-input input{
      margin:0;
      min-width:200px;
      opacity:0; }
      .bp3-file-input input:disabled + .bp3-file-upload-input,
      .bp3-file-input input.bp3-disabled + .bp3-file-upload-input{
        background:rgba(206, 217, 224, 0.5);
        -webkit-box-shadow:none;
                box-shadow:none;
        color:rgba(92, 112, 128, 0.6);
        cursor:not-allowed;
        resize:none; }
        .bp3-file-input input:disabled + .bp3-file-upload-input::after,
        .bp3-file-input input.bp3-disabled + .bp3-file-upload-input::after{
          background-color:rgba(206, 217, 224, 0.5);
          background-image:none;
          -webkit-box-shadow:none;
                  box-shadow:none;
          color:rgba(92, 112, 128, 0.6);
          cursor:not-allowed;
          outline:none; }
          .bp3-file-input input:disabled + .bp3-file-upload-input::after.bp3-active, .bp3-file-input input:disabled + .bp3-file-upload-input::after.bp3-active:hover,
          .bp3-file-input input.bp3-disabled + .bp3-file-upload-input::after.bp3-active,
          .bp3-file-input input.bp3-disabled + .bp3-file-upload-input::after.bp3-active:hover{
            background:rgba(206, 217, 224, 0.7); }
        .bp3-dark .bp3-file-input input:disabled + .bp3-file-upload-input, .bp3-dark
        .bp3-file-input input.bp3-disabled + .bp3-file-upload-input{
          background:rgba(57, 75, 89, 0.5);
          -webkit-box-shadow:none;
                  box-shadow:none;
          color:rgba(167, 182, 194, 0.6); }
          .bp3-dark .bp3-file-input input:disabled + .bp3-file-upload-input::after, .bp3-dark
          .bp3-file-input input.bp3-disabled + .bp3-file-upload-input::after{
            background-color:rgba(57, 75, 89, 0.5);
            background-image:none;
            -webkit-box-shadow:none;
                    box-shadow:none;
            color:rgba(167, 182, 194, 0.6); }
            .bp3-dark .bp3-file-input input:disabled + .bp3-file-upload-input::after.bp3-active, .bp3-dark
            .bp3-file-input input.bp3-disabled + .bp3-file-upload-input::after.bp3-active{
              background:rgba(57, 75, 89, 0.7); }
    .bp3-file-input.bp3-file-input-has-selection .bp3-file-upload-input{
      color:#182026; }
    .bp3-dark .bp3-file-input.bp3-file-input-has-selection .bp3-file-upload-input{
      color:#f5f8fa; }
    .bp3-file-input.bp3-fill{
      width:100%; }
    .bp3-file-input.bp3-large,
    .bp3-large .bp3-file-input{
      height:40px; }
    .bp3-file-input .bp3-file-upload-input-custom-text::after{
      content:attr(bp3-button-text); }

  .bp3-file-upload-input{
    -webkit-appearance:none;
      -moz-appearance:none;
            appearance:none;
    background:#ffffff;
    border:none;
    border-radius:3px;
    -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
    color:#182026;
    font-size:14px;
    font-weight:400;
    height:30px;
    line-height:30px;
    outline:none;
    padding:0 10px;
    -webkit-transition:-webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:-webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
    vertical-align:middle;
    overflow:hidden;
    text-overflow:ellipsis;
    white-space:nowrap;
    word-wrap:normal;
    color:rgba(92, 112, 128, 0.6);
    left:0;
    padding-right:80px;
    position:absolute;
    right:0;
    top:0;
    -webkit-user-select:none;
      -moz-user-select:none;
        -ms-user-select:none;
            user-select:none; }
    .bp3-file-upload-input::-webkit-input-placeholder{
      color:rgba(92, 112, 128, 0.6);
      opacity:1; }
    .bp3-file-upload-input::-moz-placeholder{
      color:rgba(92, 112, 128, 0.6);
      opacity:1; }
    .bp3-file-upload-input:-ms-input-placeholder{
      color:rgba(92, 112, 128, 0.6);
      opacity:1; }
    .bp3-file-upload-input::-ms-input-placeholder{
      color:rgba(92, 112, 128, 0.6);
      opacity:1; }
    .bp3-file-upload-input::placeholder{
      color:rgba(92, 112, 128, 0.6);
      opacity:1; }
    .bp3-file-upload-input:focus, .bp3-file-upload-input.bp3-active{
      -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-file-upload-input[type="search"], .bp3-file-upload-input.bp3-round{
      border-radius:30px;
      -webkit-box-sizing:border-box;
              box-sizing:border-box;
      padding-left:10px; }
    .bp3-file-upload-input[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.15);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.15); }
    .bp3-file-upload-input:disabled, .bp3-file-upload-input.bp3-disabled{
      background:rgba(206, 217, 224, 0.5);
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(92, 112, 128, 0.6);
      cursor:not-allowed;
      resize:none; }
    .bp3-file-upload-input::after{
      background-color:#f5f8fa;
      background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.8)), to(rgba(255, 255, 255, 0)));
      background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.8), rgba(255, 255, 255, 0));
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
      color:#182026;
      min-height:24px;
      min-width:24px;
      overflow:hidden;
      text-overflow:ellipsis;
      white-space:nowrap;
      word-wrap:normal;
      border-radius:3px;
      content:"Browse";
      line-height:24px;
      margin:3px;
      position:absolute;
      right:0;
      text-align:center;
      top:0;
      width:70px; }
      .bp3-file-upload-input::after:hover{
        background-clip:padding-box;
        background-color:#ebf1f5;
        -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
                box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1); }
      .bp3-file-upload-input::after:active, .bp3-file-upload-input::after.bp3-active{
        background-color:#d8e1e8;
        background-image:none;
        -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
                box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
      .bp3-file-upload-input::after:disabled, .bp3-file-upload-input::after.bp3-disabled{
        background-color:rgba(206, 217, 224, 0.5);
        background-image:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:rgba(92, 112, 128, 0.6);
        cursor:not-allowed;
        outline:none; }
        .bp3-file-upload-input::after:disabled.bp3-active, .bp3-file-upload-input::after:disabled.bp3-active:hover, .bp3-file-upload-input::after.bp3-disabled.bp3-active, .bp3-file-upload-input::after.bp3-disabled.bp3-active:hover{
          background:rgba(206, 217, 224, 0.7); }
    .bp3-file-upload-input:hover::after{
      background-clip:padding-box;
      background-color:#ebf1f5;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1); }
    .bp3-file-upload-input:active::after{
      background-color:#d8e1e8;
      background-image:none;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
    .bp3-large .bp3-file-upload-input{
      font-size:16px;
      height:40px;
      line-height:40px;
      padding-right:95px; }
      .bp3-large .bp3-file-upload-input[type="search"], .bp3-large .bp3-file-upload-input.bp3-round{
        padding:0 15px; }
      .bp3-large .bp3-file-upload-input::after{
        min-height:30px;
        min-width:30px;
        line-height:30px;
        margin:5px;
        width:85px; }
    .bp3-dark .bp3-file-upload-input{
      background:rgba(16, 22, 26, 0.3);
      -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
      color:#f5f8fa;
      color:rgba(167, 182, 194, 0.6); }
      .bp3-dark .bp3-file-upload-input::-webkit-input-placeholder{
        color:rgba(167, 182, 194, 0.6); }
      .bp3-dark .bp3-file-upload-input::-moz-placeholder{
        color:rgba(167, 182, 194, 0.6); }
      .bp3-dark .bp3-file-upload-input:-ms-input-placeholder{
        color:rgba(167, 182, 194, 0.6); }
      .bp3-dark .bp3-file-upload-input::-ms-input-placeholder{
        color:rgba(167, 182, 194, 0.6); }
      .bp3-dark .bp3-file-upload-input::placeholder{
        color:rgba(167, 182, 194, 0.6); }
      .bp3-dark .bp3-file-upload-input:focus{
        -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
                box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-file-upload-input[readonly]{
        -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4);
                box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-file-upload-input:disabled, .bp3-dark .bp3-file-upload-input.bp3-disabled{
        background:rgba(57, 75, 89, 0.5);
        -webkit-box-shadow:none;
                box-shadow:none;
        color:rgba(167, 182, 194, 0.6); }
      .bp3-dark .bp3-file-upload-input::after{
        background-color:#394b59;
        background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.05)), to(rgba(255, 255, 255, 0)));
        background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.05), rgba(255, 255, 255, 0));
        -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
                box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
        color:#f5f8fa; }
        .bp3-dark .bp3-file-upload-input::after:hover, .bp3-dark .bp3-file-upload-input::after:active, .bp3-dark .bp3-file-upload-input::after.bp3-active{
          color:#f5f8fa; }
        .bp3-dark .bp3-file-upload-input::after:hover{
          background-color:#30404d;
          -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
                  box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
        .bp3-dark .bp3-file-upload-input::after:active, .bp3-dark .bp3-file-upload-input::after.bp3-active{
          background-color:#202b33;
          background-image:none;
          -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2);
                  box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
        .bp3-dark .bp3-file-upload-input::after:disabled, .bp3-dark .bp3-file-upload-input::after.bp3-disabled{
          background-color:rgba(57, 75, 89, 0.5);
          background-image:none;
          -webkit-box-shadow:none;
                  box-shadow:none;
          color:rgba(167, 182, 194, 0.6); }
          .bp3-dark .bp3-file-upload-input::after:disabled.bp3-active, .bp3-dark .bp3-file-upload-input::after.bp3-disabled.bp3-active{
            background:rgba(57, 75, 89, 0.7); }
        .bp3-dark .bp3-file-upload-input::after .bp3-button-spinner .bp3-spinner-head{
          background:rgba(16, 22, 26, 0.5);
          stroke:#8a9ba8; }
      .bp3-dark .bp3-file-upload-input:hover::after{
        background-color:#30404d;
        -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
                box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-file-upload-input:active::after{
        background-color:#202b33;
        background-image:none;
        -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2);
                box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
  .bp3-file-upload-input::after{
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1); }
  .bp3-form-group{
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    -webkit-box-orient:vertical;
    -webkit-box-direction:normal;
        -ms-flex-direction:column;
            flex-direction:column;
    margin:0 0 15px; }
    .bp3-form-group label.bp3-label{
      margin-bottom:5px; }
    .bp3-form-group .bp3-control{
      margin-top:7px; }
    .bp3-form-group .bp3-form-helper-text{
      color:#5c7080;
      font-size:12px;
      margin-top:5px; }
    .bp3-form-group.bp3-intent-primary .bp3-form-helper-text{
      color:#106ba3; }
    .bp3-form-group.bp3-intent-success .bp3-form-helper-text{
      color:#0d8050; }
    .bp3-form-group.bp3-intent-warning .bp3-form-helper-text{
      color:#bf7326; }
    .bp3-form-group.bp3-intent-danger .bp3-form-helper-text{
      color:#c23030; }
    .bp3-form-group.bp3-inline{
      -webkit-box-align:start;
          -ms-flex-align:start;
              align-items:flex-start;
      -webkit-box-orient:horizontal;
      -webkit-box-direction:normal;
          -ms-flex-direction:row;
              flex-direction:row; }
      .bp3-form-group.bp3-inline.bp3-large label.bp3-label{
        line-height:40px;
        margin:0 10px 0 0; }
      .bp3-form-group.bp3-inline label.bp3-label{
        line-height:30px;
        margin:0 10px 0 0; }
    .bp3-form-group.bp3-disabled .bp3-label,
    .bp3-form-group.bp3-disabled .bp3-text-muted,
    .bp3-form-group.bp3-disabled .bp3-form-helper-text{
      color:rgba(92, 112, 128, 0.6) !important; }
    .bp3-dark .bp3-form-group.bp3-intent-primary .bp3-form-helper-text{
      color:#48aff0; }
    .bp3-dark .bp3-form-group.bp3-intent-success .bp3-form-helper-text{
      color:#3dcc91; }
    .bp3-dark .bp3-form-group.bp3-intent-warning .bp3-form-helper-text{
      color:#ffb366; }
    .bp3-dark .bp3-form-group.bp3-intent-danger .bp3-form-helper-text{
      color:#ff7373; }
    .bp3-dark .bp3-form-group .bp3-form-helper-text{
      color:#a7b6c2; }
    .bp3-dark .bp3-form-group.bp3-disabled .bp3-label,
    .bp3-dark .bp3-form-group.bp3-disabled .bp3-text-muted,
    .bp3-dark .bp3-form-group.bp3-disabled .bp3-form-helper-text{
      color:rgba(167, 182, 194, 0.6) !important; }
  .bp3-input-group{
    display:block;
    position:relative; }
    .bp3-input-group .bp3-input{
      position:relative;
      width:100%; }
      .bp3-input-group .bp3-input:not(:first-child){
        padding-left:30px; }
      .bp3-input-group .bp3-input:not(:last-child){
        padding-right:30px; }
    .bp3-input-group .bp3-input-action,
    .bp3-input-group > .bp3-input-left-container,
    .bp3-input-group > .bp3-button,
    .bp3-input-group > .bp3-icon{
      position:absolute;
      top:0; }
      .bp3-input-group .bp3-input-action:first-child,
      .bp3-input-group > .bp3-input-left-container:first-child,
      .bp3-input-group > .bp3-button:first-child,
      .bp3-input-group > .bp3-icon:first-child{
        left:0; }
      .bp3-input-group .bp3-input-action:last-child,
      .bp3-input-group > .bp3-input-left-container:last-child,
      .bp3-input-group > .bp3-button:last-child,
      .bp3-input-group > .bp3-icon:last-child{
        right:0; }
    .bp3-input-group .bp3-button{
      min-height:24px;
      min-width:24px;
      margin:3px;
      padding:0 7px; }
      .bp3-input-group .bp3-button:empty{
        padding:0; }
    .bp3-input-group > .bp3-input-left-container,
    .bp3-input-group > .bp3-icon{
      z-index:1; }
    .bp3-input-group > .bp3-input-left-container > .bp3-icon,
    .bp3-input-group > .bp3-icon{
      color:#5c7080; }
      .bp3-input-group > .bp3-input-left-container > .bp3-icon:empty,
      .bp3-input-group > .bp3-icon:empty{
        font-family:"Icons16", sans-serif;
        font-size:16px;
        font-style:normal;
        font-weight:400;
        line-height:1;
        -moz-osx-font-smoothing:grayscale;
        -webkit-font-smoothing:antialiased; }
    .bp3-input-group > .bp3-input-left-container > .bp3-icon,
    .bp3-input-group > .bp3-icon,
    .bp3-input-group .bp3-input-action > .bp3-spinner{
      margin:7px; }
    .bp3-input-group .bp3-tag{
      margin:5px; }
    .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:not(:hover):not(:focus),
    .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:not(:hover):not(:focus){
      color:#5c7080; }
      .bp3-dark .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:not(:hover):not(:focus), .bp3-dark
      .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:not(:hover):not(:focus){
        color:#a7b6c2; }
      .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:not(:hover):not(:focus) .bp3-icon, .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:not(:hover):not(:focus) .bp3-icon-standard, .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:not(:hover):not(:focus) .bp3-icon-large,
      .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:not(:hover):not(:focus) .bp3-icon,
      .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:not(:hover):not(:focus) .bp3-icon-standard,
      .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:not(:hover):not(:focus) .bp3-icon-large{
        color:#5c7080; }
    .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:disabled,
    .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:disabled{
      color:rgba(92, 112, 128, 0.6) !important; }
      .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:disabled .bp3-icon, .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:disabled .bp3-icon-standard, .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:disabled .bp3-icon-large,
      .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:disabled .bp3-icon,
      .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:disabled .bp3-icon-standard,
      .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:disabled .bp3-icon-large{
        color:rgba(92, 112, 128, 0.6) !important; }
    .bp3-input-group.bp3-disabled{
      cursor:not-allowed; }
      .bp3-input-group.bp3-disabled .bp3-icon{
        color:rgba(92, 112, 128, 0.6); }
    .bp3-input-group.bp3-large .bp3-button{
      min-height:30px;
      min-width:30px;
      margin:5px; }
    .bp3-input-group.bp3-large > .bp3-input-left-container > .bp3-icon,
    .bp3-input-group.bp3-large > .bp3-icon,
    .bp3-input-group.bp3-large .bp3-input-action > .bp3-spinner{
      margin:12px; }
    .bp3-input-group.bp3-large .bp3-input{
      font-size:16px;
      height:40px;
      line-height:40px; }
      .bp3-input-group.bp3-large .bp3-input[type="search"], .bp3-input-group.bp3-large .bp3-input.bp3-round{
        padding:0 15px; }
      .bp3-input-group.bp3-large .bp3-input:not(:first-child){
        padding-left:40px; }
      .bp3-input-group.bp3-large .bp3-input:not(:last-child){
        padding-right:40px; }
    .bp3-input-group.bp3-small .bp3-button{
      min-height:20px;
      min-width:20px;
      margin:2px; }
    .bp3-input-group.bp3-small .bp3-tag{
      min-height:20px;
      min-width:20px;
      margin:2px; }
    .bp3-input-group.bp3-small > .bp3-input-left-container > .bp3-icon,
    .bp3-input-group.bp3-small > .bp3-icon,
    .bp3-input-group.bp3-small .bp3-input-action > .bp3-spinner{
      margin:4px; }
    .bp3-input-group.bp3-small .bp3-input{
      font-size:12px;
      height:24px;
      line-height:24px;
      padding-left:8px;
      padding-right:8px; }
      .bp3-input-group.bp3-small .bp3-input[type="search"], .bp3-input-group.bp3-small .bp3-input.bp3-round{
        padding:0 12px; }
      .bp3-input-group.bp3-small .bp3-input:not(:first-child){
        padding-left:24px; }
      .bp3-input-group.bp3-small .bp3-input:not(:last-child){
        padding-right:24px; }
    .bp3-input-group.bp3-fill{
      -webkit-box-flex:1;
          -ms-flex:1 1 auto;
              flex:1 1 auto;
      width:100%; }
    .bp3-input-group.bp3-round .bp3-button,
    .bp3-input-group.bp3-round .bp3-input,
    .bp3-input-group.bp3-round .bp3-tag{
      border-radius:30px; }
    .bp3-dark .bp3-input-group .bp3-icon{
      color:#a7b6c2; }
    .bp3-dark .bp3-input-group.bp3-disabled .bp3-icon{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-input-group.bp3-intent-primary .bp3-input{
      -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px #137cbd, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px #137cbd, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
      .bp3-input-group.bp3-intent-primary .bp3-input:focus{
        -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
                box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
      .bp3-input-group.bp3-intent-primary .bp3-input[readonly]{
        -webkit-box-shadow:inset 0 0 0 1px #137cbd;
                box-shadow:inset 0 0 0 1px #137cbd; }
      .bp3-input-group.bp3-intent-primary .bp3-input:disabled, .bp3-input-group.bp3-intent-primary .bp3-input.bp3-disabled{
        -webkit-box-shadow:none;
                box-shadow:none; }
    .bp3-input-group.bp3-intent-primary > .bp3-icon{
      color:#106ba3; }
      .bp3-dark .bp3-input-group.bp3-intent-primary > .bp3-icon{
        color:#48aff0; }
    .bp3-input-group.bp3-intent-success .bp3-input{
      -webkit-box-shadow:0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), inset 0 0 0 1px #0f9960, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), inset 0 0 0 1px #0f9960, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
      .bp3-input-group.bp3-intent-success .bp3-input:focus{
        -webkit-box-shadow:0 0 0 1px #0f9960, 0 0 0 3px rgba(15, 153, 96, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
                box-shadow:0 0 0 1px #0f9960, 0 0 0 3px rgba(15, 153, 96, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
      .bp3-input-group.bp3-intent-success .bp3-input[readonly]{
        -webkit-box-shadow:inset 0 0 0 1px #0f9960;
                box-shadow:inset 0 0 0 1px #0f9960; }
      .bp3-input-group.bp3-intent-success .bp3-input:disabled, .bp3-input-group.bp3-intent-success .bp3-input.bp3-disabled{
        -webkit-box-shadow:none;
                box-shadow:none; }
    .bp3-input-group.bp3-intent-success > .bp3-icon{
      color:#0d8050; }
      .bp3-dark .bp3-input-group.bp3-intent-success > .bp3-icon{
        color:#3dcc91; }
    .bp3-input-group.bp3-intent-warning .bp3-input{
      -webkit-box-shadow:0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), inset 0 0 0 1px #d9822b, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), inset 0 0 0 1px #d9822b, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
      .bp3-input-group.bp3-intent-warning .bp3-input:focus{
        -webkit-box-shadow:0 0 0 1px #d9822b, 0 0 0 3px rgba(217, 130, 43, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
                box-shadow:0 0 0 1px #d9822b, 0 0 0 3px rgba(217, 130, 43, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
      .bp3-input-group.bp3-intent-warning .bp3-input[readonly]{
        -webkit-box-shadow:inset 0 0 0 1px #d9822b;
                box-shadow:inset 0 0 0 1px #d9822b; }
      .bp3-input-group.bp3-intent-warning .bp3-input:disabled, .bp3-input-group.bp3-intent-warning .bp3-input.bp3-disabled{
        -webkit-box-shadow:none;
                box-shadow:none; }
    .bp3-input-group.bp3-intent-warning > .bp3-icon{
      color:#bf7326; }
      .bp3-dark .bp3-input-group.bp3-intent-warning > .bp3-icon{
        color:#ffb366; }
    .bp3-input-group.bp3-intent-danger .bp3-input{
      -webkit-box-shadow:0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), inset 0 0 0 1px #db3737, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), inset 0 0 0 1px #db3737, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
      .bp3-input-group.bp3-intent-danger .bp3-input:focus{
        -webkit-box-shadow:0 0 0 1px #db3737, 0 0 0 3px rgba(219, 55, 55, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
                box-shadow:0 0 0 1px #db3737, 0 0 0 3px rgba(219, 55, 55, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
      .bp3-input-group.bp3-intent-danger .bp3-input[readonly]{
        -webkit-box-shadow:inset 0 0 0 1px #db3737;
                box-shadow:inset 0 0 0 1px #db3737; }
      .bp3-input-group.bp3-intent-danger .bp3-input:disabled, .bp3-input-group.bp3-intent-danger .bp3-input.bp3-disabled{
        -webkit-box-shadow:none;
                box-shadow:none; }
    .bp3-input-group.bp3-intent-danger > .bp3-icon{
      color:#c23030; }
      .bp3-dark .bp3-input-group.bp3-intent-danger > .bp3-icon{
        color:#ff7373; }
  .bp3-input{
    -webkit-appearance:none;
      -moz-appearance:none;
            appearance:none;
    background:#ffffff;
    border:none;
    border-radius:3px;
    -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
    color:#182026;
    font-size:14px;
    font-weight:400;
    height:30px;
    line-height:30px;
    outline:none;
    padding:0 10px;
    -webkit-transition:-webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:-webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
    vertical-align:middle; }
    .bp3-input::-webkit-input-placeholder{
      color:rgba(92, 112, 128, 0.6);
      opacity:1; }
    .bp3-input::-moz-placeholder{
      color:rgba(92, 112, 128, 0.6);
      opacity:1; }
    .bp3-input:-ms-input-placeholder{
      color:rgba(92, 112, 128, 0.6);
      opacity:1; }
    .bp3-input::-ms-input-placeholder{
      color:rgba(92, 112, 128, 0.6);
      opacity:1; }
    .bp3-input::placeholder{
      color:rgba(92, 112, 128, 0.6);
      opacity:1; }
    .bp3-input:focus, .bp3-input.bp3-active{
      -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input[type="search"], .bp3-input.bp3-round{
      border-radius:30px;
      -webkit-box-sizing:border-box;
              box-sizing:border-box;
      padding-left:10px; }
    .bp3-input[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.15);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.15); }
    .bp3-input:disabled, .bp3-input.bp3-disabled{
      background:rgba(206, 217, 224, 0.5);
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(92, 112, 128, 0.6);
      cursor:not-allowed;
      resize:none; }
    .bp3-input.bp3-large{
      font-size:16px;
      height:40px;
      line-height:40px; }
      .bp3-input.bp3-large[type="search"], .bp3-input.bp3-large.bp3-round{
        padding:0 15px; }
    .bp3-input.bp3-small{
      font-size:12px;
      height:24px;
      line-height:24px;
      padding-left:8px;
      padding-right:8px; }
      .bp3-input.bp3-small[type="search"], .bp3-input.bp3-small.bp3-round{
        padding:0 12px; }
    .bp3-input.bp3-fill{
      -webkit-box-flex:1;
          -ms-flex:1 1 auto;
              flex:1 1 auto;
      width:100%; }
    .bp3-dark .bp3-input{
      background:rgba(16, 22, 26, 0.3);
      -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
      color:#f5f8fa; }
      .bp3-dark .bp3-input::-webkit-input-placeholder{
        color:rgba(167, 182, 194, 0.6); }
      .bp3-dark .bp3-input::-moz-placeholder{
        color:rgba(167, 182, 194, 0.6); }
      .bp3-dark .bp3-input:-ms-input-placeholder{
        color:rgba(167, 182, 194, 0.6); }
      .bp3-dark .bp3-input::-ms-input-placeholder{
        color:rgba(167, 182, 194, 0.6); }
      .bp3-dark .bp3-input::placeholder{
        color:rgba(167, 182, 194, 0.6); }
      .bp3-dark .bp3-input:focus{
        -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
                box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-input[readonly]{
        -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4);
                box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-input:disabled, .bp3-dark .bp3-input.bp3-disabled{
        background:rgba(57, 75, 89, 0.5);
        -webkit-box-shadow:none;
                box-shadow:none;
        color:rgba(167, 182, 194, 0.6); }
    .bp3-input.bp3-intent-primary{
      -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px #137cbd, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px #137cbd, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
      .bp3-input.bp3-intent-primary:focus{
        -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
                box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
      .bp3-input.bp3-intent-primary[readonly]{
        -webkit-box-shadow:inset 0 0 0 1px #137cbd;
                box-shadow:inset 0 0 0 1px #137cbd; }
      .bp3-input.bp3-intent-primary:disabled, .bp3-input.bp3-intent-primary.bp3-disabled{
        -webkit-box-shadow:none;
                box-shadow:none; }
      .bp3-dark .bp3-input.bp3-intent-primary{
        -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px #137cbd, inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
                box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px #137cbd, inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
        .bp3-dark .bp3-input.bp3-intent-primary:focus{
          -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
                  box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
        .bp3-dark .bp3-input.bp3-intent-primary[readonly]{
          -webkit-box-shadow:inset 0 0 0 1px #137cbd;
                  box-shadow:inset 0 0 0 1px #137cbd; }
        .bp3-dark .bp3-input.bp3-intent-primary:disabled, .bp3-dark .bp3-input.bp3-intent-primary.bp3-disabled{
          -webkit-box-shadow:none;
                  box-shadow:none; }
    .bp3-input.bp3-intent-success{
      -webkit-box-shadow:0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), inset 0 0 0 1px #0f9960, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), inset 0 0 0 1px #0f9960, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
      .bp3-input.bp3-intent-success:focus{
        -webkit-box-shadow:0 0 0 1px #0f9960, 0 0 0 3px rgba(15, 153, 96, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
                box-shadow:0 0 0 1px #0f9960, 0 0 0 3px rgba(15, 153, 96, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
      .bp3-input.bp3-intent-success[readonly]{
        -webkit-box-shadow:inset 0 0 0 1px #0f9960;
                box-shadow:inset 0 0 0 1px #0f9960; }
      .bp3-input.bp3-intent-success:disabled, .bp3-input.bp3-intent-success.bp3-disabled{
        -webkit-box-shadow:none;
                box-shadow:none; }
      .bp3-dark .bp3-input.bp3-intent-success{
        -webkit-box-shadow:0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), inset 0 0 0 1px #0f9960, inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
                box-shadow:0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), inset 0 0 0 1px #0f9960, inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
        .bp3-dark .bp3-input.bp3-intent-success:focus{
          -webkit-box-shadow:0 0 0 1px #0f9960, 0 0 0 1px #0f9960, 0 0 0 3px rgba(15, 153, 96, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
                  box-shadow:0 0 0 1px #0f9960, 0 0 0 1px #0f9960, 0 0 0 3px rgba(15, 153, 96, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
        .bp3-dark .bp3-input.bp3-intent-success[readonly]{
          -webkit-box-shadow:inset 0 0 0 1px #0f9960;
                  box-shadow:inset 0 0 0 1px #0f9960; }
        .bp3-dark .bp3-input.bp3-intent-success:disabled, .bp3-dark .bp3-input.bp3-intent-success.bp3-disabled{
          -webkit-box-shadow:none;
                  box-shadow:none; }
    .bp3-input.bp3-intent-warning{
      -webkit-box-shadow:0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), inset 0 0 0 1px #d9822b, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), inset 0 0 0 1px #d9822b, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
      .bp3-input.bp3-intent-warning:focus{
        -webkit-box-shadow:0 0 0 1px #d9822b, 0 0 0 3px rgba(217, 130, 43, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
                box-shadow:0 0 0 1px #d9822b, 0 0 0 3px rgba(217, 130, 43, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
      .bp3-input.bp3-intent-warning[readonly]{
        -webkit-box-shadow:inset 0 0 0 1px #d9822b;
                box-shadow:inset 0 0 0 1px #d9822b; }
      .bp3-input.bp3-intent-warning:disabled, .bp3-input.bp3-intent-warning.bp3-disabled{
        -webkit-box-shadow:none;
                box-shadow:none; }
      .bp3-dark .bp3-input.bp3-intent-warning{
        -webkit-box-shadow:0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), inset 0 0 0 1px #d9822b, inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
                box-shadow:0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), inset 0 0 0 1px #d9822b, inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
        .bp3-dark .bp3-input.bp3-intent-warning:focus{
          -webkit-box-shadow:0 0 0 1px #d9822b, 0 0 0 1px #d9822b, 0 0 0 3px rgba(217, 130, 43, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
                  box-shadow:0 0 0 1px #d9822b, 0 0 0 1px #d9822b, 0 0 0 3px rgba(217, 130, 43, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
        .bp3-dark .bp3-input.bp3-intent-warning[readonly]{
          -webkit-box-shadow:inset 0 0 0 1px #d9822b;
                  box-shadow:inset 0 0 0 1px #d9822b; }
        .bp3-dark .bp3-input.bp3-intent-warning:disabled, .bp3-dark .bp3-input.bp3-intent-warning.bp3-disabled{
          -webkit-box-shadow:none;
                  box-shadow:none; }
    .bp3-input.bp3-intent-danger{
      -webkit-box-shadow:0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), inset 0 0 0 1px #db3737, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), inset 0 0 0 1px #db3737, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
      .bp3-input.bp3-intent-danger:focus{
        -webkit-box-shadow:0 0 0 1px #db3737, 0 0 0 3px rgba(219, 55, 55, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
                box-shadow:0 0 0 1px #db3737, 0 0 0 3px rgba(219, 55, 55, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
      .bp3-input.bp3-intent-danger[readonly]{
        -webkit-box-shadow:inset 0 0 0 1px #db3737;
                box-shadow:inset 0 0 0 1px #db3737; }
      .bp3-input.bp3-intent-danger:disabled, .bp3-input.bp3-intent-danger.bp3-disabled{
        -webkit-box-shadow:none;
                box-shadow:none; }
      .bp3-dark .bp3-input.bp3-intent-danger{
        -webkit-box-shadow:0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), inset 0 0 0 1px #db3737, inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
                box-shadow:0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), inset 0 0 0 1px #db3737, inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
        .bp3-dark .bp3-input.bp3-intent-danger:focus{
          -webkit-box-shadow:0 0 0 1px #db3737, 0 0 0 1px #db3737, 0 0 0 3px rgba(219, 55, 55, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
                  box-shadow:0 0 0 1px #db3737, 0 0 0 1px #db3737, 0 0 0 3px rgba(219, 55, 55, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
        .bp3-dark .bp3-input.bp3-intent-danger[readonly]{
          -webkit-box-shadow:inset 0 0 0 1px #db3737;
                  box-shadow:inset 0 0 0 1px #db3737; }
        .bp3-dark .bp3-input.bp3-intent-danger:disabled, .bp3-dark .bp3-input.bp3-intent-danger.bp3-disabled{
          -webkit-box-shadow:none;
                  box-shadow:none; }
    .bp3-input::-ms-clear{
      display:none; }
  textarea.bp3-input{
    max-width:100%;
    padding:10px; }
    textarea.bp3-input, textarea.bp3-input.bp3-large, textarea.bp3-input.bp3-small{
      height:auto;
      line-height:inherit; }
    textarea.bp3-input.bp3-small{
      padding:8px; }
    .bp3-dark textarea.bp3-input{
      background:rgba(16, 22, 26, 0.3);
      -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
      color:#f5f8fa; }
      .bp3-dark textarea.bp3-input::-webkit-input-placeholder{
        color:rgba(167, 182, 194, 0.6); }
      .bp3-dark textarea.bp3-input::-moz-placeholder{
        color:rgba(167, 182, 194, 0.6); }
      .bp3-dark textarea.bp3-input:-ms-input-placeholder{
        color:rgba(167, 182, 194, 0.6); }
      .bp3-dark textarea.bp3-input::-ms-input-placeholder{
        color:rgba(167, 182, 194, 0.6); }
      .bp3-dark textarea.bp3-input::placeholder{
        color:rgba(167, 182, 194, 0.6); }
      .bp3-dark textarea.bp3-input:focus{
        -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
                box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark textarea.bp3-input[readonly]{
        -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4);
                box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark textarea.bp3-input:disabled, .bp3-dark textarea.bp3-input.bp3-disabled{
        background:rgba(57, 75, 89, 0.5);
        -webkit-box-shadow:none;
                box-shadow:none;
        color:rgba(167, 182, 194, 0.6); }
  label.bp3-label{
    display:block;
    margin-bottom:15px;
    margin-top:0; }
    label.bp3-label .bp3-html-select,
    label.bp3-label .bp3-input,
    label.bp3-label .bp3-select,
    label.bp3-label .bp3-slider,
    label.bp3-label .bp3-popover-wrapper{
      display:block;
      margin-top:5px;
      text-transform:none; }
    label.bp3-label .bp3-button-group{
      margin-top:5px; }
    label.bp3-label .bp3-select select,
    label.bp3-label .bp3-html-select select{
      font-weight:400;
      vertical-align:top;
      width:100%; }
    label.bp3-label.bp3-disabled,
    label.bp3-label.bp3-disabled .bp3-text-muted{
      color:rgba(92, 112, 128, 0.6); }
    label.bp3-label.bp3-inline{
      line-height:30px; }
      label.bp3-label.bp3-inline .bp3-html-select,
      label.bp3-label.bp3-inline .bp3-input,
      label.bp3-label.bp3-inline .bp3-input-group,
      label.bp3-label.bp3-inline .bp3-select,
      label.bp3-label.bp3-inline .bp3-popover-wrapper{
        display:inline-block;
        margin:0 0 0 5px;
        vertical-align:top; }
      label.bp3-label.bp3-inline .bp3-button-group{
        margin:0 0 0 5px; }
      label.bp3-label.bp3-inline .bp3-input-group .bp3-input{
        margin-left:0; }
      label.bp3-label.bp3-inline.bp3-large{
        line-height:40px; }
    label.bp3-label:not(.bp3-inline) .bp3-popover-target{
      display:block; }
    .bp3-dark label.bp3-label{
      color:#f5f8fa; }
      .bp3-dark label.bp3-label.bp3-disabled,
      .bp3-dark label.bp3-label.bp3-disabled .bp3-text-muted{
        color:rgba(167, 182, 194, 0.6); }
  .bp3-numeric-input .bp3-button-group.bp3-vertical > .bp3-button{
    -webkit-box-flex:1;
        -ms-flex:1 1 14px;
            flex:1 1 14px;
    min-height:0;
    padding:0;
    width:30px; }
    .bp3-numeric-input .bp3-button-group.bp3-vertical > .bp3-button:first-child{
      border-radius:0 3px 0 0; }
    .bp3-numeric-input .bp3-button-group.bp3-vertical > .bp3-button:last-child{
      border-radius:0 0 3px 0; }

  .bp3-numeric-input .bp3-button-group.bp3-vertical:first-child > .bp3-button:first-child{
    border-radius:3px 0 0 0; }

  .bp3-numeric-input .bp3-button-group.bp3-vertical:first-child > .bp3-button:last-child{
    border-radius:0 0 0 3px; }

  .bp3-numeric-input.bp3-large .bp3-button-group.bp3-vertical > .bp3-button{
    width:40px; }

  form{
    display:block; }
  .bp3-html-select select,
  .bp3-select select{
    display:-webkit-inline-box;
    display:-ms-inline-flexbox;
    display:inline-flex;
    -webkit-box-orient:horizontal;
    -webkit-box-direction:normal;
        -ms-flex-direction:row;
            flex-direction:row;
    -webkit-box-align:center;
        -ms-flex-align:center;
            align-items:center;
    border:none;
    border-radius:3px;
    cursor:pointer;
    font-size:14px;
    -webkit-box-pack:center;
        -ms-flex-pack:center;
            justify-content:center;
    padding:5px 10px;
    text-align:left;
    vertical-align:middle;
    background-color:#f5f8fa;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.8)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.8), rgba(255, 255, 255, 0));
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
    color:#182026;
    -moz-appearance:none;
    -webkit-appearance:none;
    border-radius:3px;
    height:30px;
    padding:0 25px 0 10px;
    width:100%; }
    .bp3-html-select select > *, .bp3-select select > *{
      -webkit-box-flex:0;
          -ms-flex-positive:0;
              flex-grow:0;
      -ms-flex-negative:0;
          flex-shrink:0; }
    .bp3-html-select select > .bp3-fill, .bp3-select select > .bp3-fill{
      -webkit-box-flex:1;
          -ms-flex-positive:1;
              flex-grow:1;
      -ms-flex-negative:1;
          flex-shrink:1; }
    .bp3-html-select select::before,
    .bp3-select select::before, .bp3-html-select select > *, .bp3-select select > *{
      margin-right:7px; }
    .bp3-html-select select:empty::before,
    .bp3-select select:empty::before,
    .bp3-html-select select > :last-child,
    .bp3-select select > :last-child{
      margin-right:0; }
    .bp3-html-select select:hover,
    .bp3-select select:hover{
      background-clip:padding-box;
      background-color:#ebf1f5;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1); }
    .bp3-html-select select:active,
    .bp3-select select:active, .bp3-html-select select.bp3-active,
    .bp3-select select.bp3-active{
      background-color:#d8e1e8;
      background-image:none;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
    .bp3-html-select select:disabled,
    .bp3-select select:disabled, .bp3-html-select select.bp3-disabled,
    .bp3-select select.bp3-disabled{
      background-color:rgba(206, 217, 224, 0.5);
      background-image:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(92, 112, 128, 0.6);
      cursor:not-allowed;
      outline:none; }
      .bp3-html-select select:disabled.bp3-active,
      .bp3-select select:disabled.bp3-active, .bp3-html-select select:disabled.bp3-active:hover,
      .bp3-select select:disabled.bp3-active:hover, .bp3-html-select select.bp3-disabled.bp3-active,
      .bp3-select select.bp3-disabled.bp3-active, .bp3-html-select select.bp3-disabled.bp3-active:hover,
      .bp3-select select.bp3-disabled.bp3-active:hover{
        background:rgba(206, 217, 224, 0.7); }

  .bp3-html-select.bp3-minimal select,
  .bp3-select.bp3-minimal select{
    background:none;
    -webkit-box-shadow:none;
            box-shadow:none; }
    .bp3-html-select.bp3-minimal select:hover,
    .bp3-select.bp3-minimal select:hover{
      background:rgba(167, 182, 194, 0.3);
      -webkit-box-shadow:none;
              box-shadow:none;
      color:#182026;
      text-decoration:none; }
    .bp3-html-select.bp3-minimal select:active,
    .bp3-select.bp3-minimal select:active, .bp3-html-select.bp3-minimal select.bp3-active,
    .bp3-select.bp3-minimal select.bp3-active{
      background:rgba(115, 134, 148, 0.3);
      -webkit-box-shadow:none;
              box-shadow:none;
      color:#182026; }
    .bp3-html-select.bp3-minimal select:disabled,
    .bp3-select.bp3-minimal select:disabled, .bp3-html-select.bp3-minimal select:disabled:hover,
    .bp3-select.bp3-minimal select:disabled:hover, .bp3-html-select.bp3-minimal select.bp3-disabled,
    .bp3-select.bp3-minimal select.bp3-disabled, .bp3-html-select.bp3-minimal select.bp3-disabled:hover,
    .bp3-select.bp3-minimal select.bp3-disabled:hover{
      background:none;
      color:rgba(92, 112, 128, 0.6);
      cursor:not-allowed; }
      .bp3-html-select.bp3-minimal select:disabled.bp3-active,
      .bp3-select.bp3-minimal select:disabled.bp3-active, .bp3-html-select.bp3-minimal select:disabled:hover.bp3-active,
      .bp3-select.bp3-minimal select:disabled:hover.bp3-active, .bp3-html-select.bp3-minimal select.bp3-disabled.bp3-active,
      .bp3-select.bp3-minimal select.bp3-disabled.bp3-active, .bp3-html-select.bp3-minimal select.bp3-disabled:hover.bp3-active,
      .bp3-select.bp3-minimal select.bp3-disabled:hover.bp3-active{
        background:rgba(115, 134, 148, 0.3); }
    .bp3-dark .bp3-html-select.bp3-minimal select, .bp3-html-select.bp3-minimal .bp3-dark select,
    .bp3-dark .bp3-select.bp3-minimal select, .bp3-select.bp3-minimal .bp3-dark select{
      background:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:inherit; }
      .bp3-dark .bp3-html-select.bp3-minimal select:hover, .bp3-html-select.bp3-minimal .bp3-dark select:hover,
      .bp3-dark .bp3-select.bp3-minimal select:hover, .bp3-select.bp3-minimal .bp3-dark select:hover, .bp3-dark .bp3-html-select.bp3-minimal select:active, .bp3-html-select.bp3-minimal .bp3-dark select:active,
      .bp3-dark .bp3-select.bp3-minimal select:active, .bp3-select.bp3-minimal .bp3-dark select:active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none; }
      .bp3-dark .bp3-html-select.bp3-minimal select:hover, .bp3-html-select.bp3-minimal .bp3-dark select:hover,
      .bp3-dark .bp3-select.bp3-minimal select:hover, .bp3-select.bp3-minimal .bp3-dark select:hover{
        background:rgba(138, 155, 168, 0.15); }
      .bp3-dark .bp3-html-select.bp3-minimal select:active, .bp3-html-select.bp3-minimal .bp3-dark select:active,
      .bp3-dark .bp3-select.bp3-minimal select:active, .bp3-select.bp3-minimal .bp3-dark select:active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-active{
        background:rgba(138, 155, 168, 0.3);
        color:#f5f8fa; }
      .bp3-dark .bp3-html-select.bp3-minimal select:disabled, .bp3-html-select.bp3-minimal .bp3-dark select:disabled,
      .bp3-dark .bp3-select.bp3-minimal select:disabled, .bp3-select.bp3-minimal .bp3-dark select:disabled, .bp3-dark .bp3-html-select.bp3-minimal select:disabled:hover, .bp3-html-select.bp3-minimal .bp3-dark select:disabled:hover,
      .bp3-dark .bp3-select.bp3-minimal select:disabled:hover, .bp3-select.bp3-minimal .bp3-dark select:disabled:hover, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-disabled,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-disabled, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-disabled:hover, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-disabled:hover,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-disabled:hover, .bp3-select.bp3-minimal .bp3-dark select.bp3-disabled:hover{
        background:none;
        color:rgba(167, 182, 194, 0.6);
        cursor:not-allowed; }
        .bp3-dark .bp3-html-select.bp3-minimal select:disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select:disabled.bp3-active,
        .bp3-dark .bp3-select.bp3-minimal select:disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select:disabled.bp3-active, .bp3-dark .bp3-html-select.bp3-minimal select:disabled:hover.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select:disabled:hover.bp3-active,
        .bp3-dark .bp3-select.bp3-minimal select:disabled:hover.bp3-active, .bp3-select.bp3-minimal .bp3-dark select:disabled:hover.bp3-active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-disabled.bp3-active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-disabled.bp3-active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-disabled:hover.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-disabled:hover.bp3-active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-disabled:hover.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-disabled:hover.bp3-active{
          background:rgba(138, 155, 168, 0.3); }
    .bp3-html-select.bp3-minimal select.bp3-intent-primary,
    .bp3-select.bp3-minimal select.bp3-intent-primary{
      color:#106ba3; }
      .bp3-html-select.bp3-minimal select.bp3-intent-primary:hover,
      .bp3-select.bp3-minimal select.bp3-intent-primary:hover, .bp3-html-select.bp3-minimal select.bp3-intent-primary:active,
      .bp3-select.bp3-minimal select.bp3-intent-primary:active, .bp3-html-select.bp3-minimal select.bp3-intent-primary.bp3-active,
      .bp3-select.bp3-minimal select.bp3-intent-primary.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#106ba3; }
      .bp3-html-select.bp3-minimal select.bp3-intent-primary:hover,
      .bp3-select.bp3-minimal select.bp3-intent-primary:hover{
        background:rgba(19, 124, 189, 0.15);
        color:#106ba3; }
      .bp3-html-select.bp3-minimal select.bp3-intent-primary:active,
      .bp3-select.bp3-minimal select.bp3-intent-primary:active, .bp3-html-select.bp3-minimal select.bp3-intent-primary.bp3-active,
      .bp3-select.bp3-minimal select.bp3-intent-primary.bp3-active{
        background:rgba(19, 124, 189, 0.3);
        color:#106ba3; }
      .bp3-html-select.bp3-minimal select.bp3-intent-primary:disabled,
      .bp3-select.bp3-minimal select.bp3-intent-primary:disabled, .bp3-html-select.bp3-minimal select.bp3-intent-primary.bp3-disabled,
      .bp3-select.bp3-minimal select.bp3-intent-primary.bp3-disabled{
        background:none;
        color:rgba(16, 107, 163, 0.5); }
        .bp3-html-select.bp3-minimal select.bp3-intent-primary:disabled.bp3-active,
        .bp3-select.bp3-minimal select.bp3-intent-primary:disabled.bp3-active, .bp3-html-select.bp3-minimal select.bp3-intent-primary.bp3-disabled.bp3-active,
        .bp3-select.bp3-minimal select.bp3-intent-primary.bp3-disabled.bp3-active{
          background:rgba(19, 124, 189, 0.3); }
      .bp3-html-select.bp3-minimal select.bp3-intent-primary .bp3-button-spinner .bp3-spinner-head, .bp3-select.bp3-minimal select.bp3-intent-primary .bp3-button-spinner .bp3-spinner-head{
        stroke:#106ba3; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-primary, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-primary,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-primary, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-primary{
        color:#48aff0; }
        .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-primary:hover, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-primary:hover,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-primary:hover, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-primary:hover{
          background:rgba(19, 124, 189, 0.2);
          color:#48aff0; }
        .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-primary:active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-primary:active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-primary:active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-primary:active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-primary.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-primary.bp3-active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-primary.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-primary.bp3-active{
          background:rgba(19, 124, 189, 0.3);
          color:#48aff0; }
        .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-primary:disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-primary:disabled,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-primary:disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-primary:disabled, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-primary.bp3-disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-primary.bp3-disabled,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-primary.bp3-disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-primary.bp3-disabled{
          background:none;
          color:rgba(72, 175, 240, 0.5); }
          .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-primary:disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-primary:disabled.bp3-active,
          .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-primary:disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-primary:disabled.bp3-active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-primary.bp3-disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-primary.bp3-disabled.bp3-active,
          .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-primary.bp3-disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-primary.bp3-disabled.bp3-active{
            background:rgba(19, 124, 189, 0.3); }
    .bp3-html-select.bp3-minimal select.bp3-intent-success,
    .bp3-select.bp3-minimal select.bp3-intent-success{
      color:#0d8050; }
      .bp3-html-select.bp3-minimal select.bp3-intent-success:hover,
      .bp3-select.bp3-minimal select.bp3-intent-success:hover, .bp3-html-select.bp3-minimal select.bp3-intent-success:active,
      .bp3-select.bp3-minimal select.bp3-intent-success:active, .bp3-html-select.bp3-minimal select.bp3-intent-success.bp3-active,
      .bp3-select.bp3-minimal select.bp3-intent-success.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#0d8050; }
      .bp3-html-select.bp3-minimal select.bp3-intent-success:hover,
      .bp3-select.bp3-minimal select.bp3-intent-success:hover{
        background:rgba(15, 153, 96, 0.15);
        color:#0d8050; }
      .bp3-html-select.bp3-minimal select.bp3-intent-success:active,
      .bp3-select.bp3-minimal select.bp3-intent-success:active, .bp3-html-select.bp3-minimal select.bp3-intent-success.bp3-active,
      .bp3-select.bp3-minimal select.bp3-intent-success.bp3-active{
        background:rgba(15, 153, 96, 0.3);
        color:#0d8050; }
      .bp3-html-select.bp3-minimal select.bp3-intent-success:disabled,
      .bp3-select.bp3-minimal select.bp3-intent-success:disabled, .bp3-html-select.bp3-minimal select.bp3-intent-success.bp3-disabled,
      .bp3-select.bp3-minimal select.bp3-intent-success.bp3-disabled{
        background:none;
        color:rgba(13, 128, 80, 0.5); }
        .bp3-html-select.bp3-minimal select.bp3-intent-success:disabled.bp3-active,
        .bp3-select.bp3-minimal select.bp3-intent-success:disabled.bp3-active, .bp3-html-select.bp3-minimal select.bp3-intent-success.bp3-disabled.bp3-active,
        .bp3-select.bp3-minimal select.bp3-intent-success.bp3-disabled.bp3-active{
          background:rgba(15, 153, 96, 0.3); }
      .bp3-html-select.bp3-minimal select.bp3-intent-success .bp3-button-spinner .bp3-spinner-head, .bp3-select.bp3-minimal select.bp3-intent-success .bp3-button-spinner .bp3-spinner-head{
        stroke:#0d8050; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-success, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-success,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-success, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-success{
        color:#3dcc91; }
        .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-success:hover, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-success:hover,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-success:hover, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-success:hover{
          background:rgba(15, 153, 96, 0.2);
          color:#3dcc91; }
        .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-success:active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-success:active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-success:active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-success:active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-success.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-success.bp3-active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-success.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-success.bp3-active{
          background:rgba(15, 153, 96, 0.3);
          color:#3dcc91; }
        .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-success:disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-success:disabled,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-success:disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-success:disabled, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-success.bp3-disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-success.bp3-disabled,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-success.bp3-disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-success.bp3-disabled{
          background:none;
          color:rgba(61, 204, 145, 0.5); }
          .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-success:disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-success:disabled.bp3-active,
          .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-success:disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-success:disabled.bp3-active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-success.bp3-disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-success.bp3-disabled.bp3-active,
          .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-success.bp3-disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-success.bp3-disabled.bp3-active{
            background:rgba(15, 153, 96, 0.3); }
    .bp3-html-select.bp3-minimal select.bp3-intent-warning,
    .bp3-select.bp3-minimal select.bp3-intent-warning{
      color:#bf7326; }
      .bp3-html-select.bp3-minimal select.bp3-intent-warning:hover,
      .bp3-select.bp3-minimal select.bp3-intent-warning:hover, .bp3-html-select.bp3-minimal select.bp3-intent-warning:active,
      .bp3-select.bp3-minimal select.bp3-intent-warning:active, .bp3-html-select.bp3-minimal select.bp3-intent-warning.bp3-active,
      .bp3-select.bp3-minimal select.bp3-intent-warning.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#bf7326; }
      .bp3-html-select.bp3-minimal select.bp3-intent-warning:hover,
      .bp3-select.bp3-minimal select.bp3-intent-warning:hover{
        background:rgba(217, 130, 43, 0.15);
        color:#bf7326; }
      .bp3-html-select.bp3-minimal select.bp3-intent-warning:active,
      .bp3-select.bp3-minimal select.bp3-intent-warning:active, .bp3-html-select.bp3-minimal select.bp3-intent-warning.bp3-active,
      .bp3-select.bp3-minimal select.bp3-intent-warning.bp3-active{
        background:rgba(217, 130, 43, 0.3);
        color:#bf7326; }
      .bp3-html-select.bp3-minimal select.bp3-intent-warning:disabled,
      .bp3-select.bp3-minimal select.bp3-intent-warning:disabled, .bp3-html-select.bp3-minimal select.bp3-intent-warning.bp3-disabled,
      .bp3-select.bp3-minimal select.bp3-intent-warning.bp3-disabled{
        background:none;
        color:rgba(191, 115, 38, 0.5); }
        .bp3-html-select.bp3-minimal select.bp3-intent-warning:disabled.bp3-active,
        .bp3-select.bp3-minimal select.bp3-intent-warning:disabled.bp3-active, .bp3-html-select.bp3-minimal select.bp3-intent-warning.bp3-disabled.bp3-active,
        .bp3-select.bp3-minimal select.bp3-intent-warning.bp3-disabled.bp3-active{
          background:rgba(217, 130, 43, 0.3); }
      .bp3-html-select.bp3-minimal select.bp3-intent-warning .bp3-button-spinner .bp3-spinner-head, .bp3-select.bp3-minimal select.bp3-intent-warning .bp3-button-spinner .bp3-spinner-head{
        stroke:#bf7326; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-warning, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-warning,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-warning, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-warning{
        color:#ffb366; }
        .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-warning:hover, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-warning:hover,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-warning:hover, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-warning:hover{
          background:rgba(217, 130, 43, 0.2);
          color:#ffb366; }
        .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-warning:active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-warning:active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-warning:active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-warning:active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-warning.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-warning.bp3-active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-warning.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-warning.bp3-active{
          background:rgba(217, 130, 43, 0.3);
          color:#ffb366; }
        .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-warning:disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-warning:disabled,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-warning:disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-warning:disabled, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-warning.bp3-disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-warning.bp3-disabled,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-warning.bp3-disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-warning.bp3-disabled{
          background:none;
          color:rgba(255, 179, 102, 0.5); }
          .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-warning:disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-warning:disabled.bp3-active,
          .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-warning:disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-warning:disabled.bp3-active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-warning.bp3-disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-warning.bp3-disabled.bp3-active,
          .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-warning.bp3-disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-warning.bp3-disabled.bp3-active{
            background:rgba(217, 130, 43, 0.3); }
    .bp3-html-select.bp3-minimal select.bp3-intent-danger,
    .bp3-select.bp3-minimal select.bp3-intent-danger{
      color:#c23030; }
      .bp3-html-select.bp3-minimal select.bp3-intent-danger:hover,
      .bp3-select.bp3-minimal select.bp3-intent-danger:hover, .bp3-html-select.bp3-minimal select.bp3-intent-danger:active,
      .bp3-select.bp3-minimal select.bp3-intent-danger:active, .bp3-html-select.bp3-minimal select.bp3-intent-danger.bp3-active,
      .bp3-select.bp3-minimal select.bp3-intent-danger.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#c23030; }
      .bp3-html-select.bp3-minimal select.bp3-intent-danger:hover,
      .bp3-select.bp3-minimal select.bp3-intent-danger:hover{
        background:rgba(219, 55, 55, 0.15);
        color:#c23030; }
      .bp3-html-select.bp3-minimal select.bp3-intent-danger:active,
      .bp3-select.bp3-minimal select.bp3-intent-danger:active, .bp3-html-select.bp3-minimal select.bp3-intent-danger.bp3-active,
      .bp3-select.bp3-minimal select.bp3-intent-danger.bp3-active{
        background:rgba(219, 55, 55, 0.3);
        color:#c23030; }
      .bp3-html-select.bp3-minimal select.bp3-intent-danger:disabled,
      .bp3-select.bp3-minimal select.bp3-intent-danger:disabled, .bp3-html-select.bp3-minimal select.bp3-intent-danger.bp3-disabled,
      .bp3-select.bp3-minimal select.bp3-intent-danger.bp3-disabled{
        background:none;
        color:rgba(194, 48, 48, 0.5); }
        .bp3-html-select.bp3-minimal select.bp3-intent-danger:disabled.bp3-active,
        .bp3-select.bp3-minimal select.bp3-intent-danger:disabled.bp3-active, .bp3-html-select.bp3-minimal select.bp3-intent-danger.bp3-disabled.bp3-active,
        .bp3-select.bp3-minimal select.bp3-intent-danger.bp3-disabled.bp3-active{
          background:rgba(219, 55, 55, 0.3); }
      .bp3-html-select.bp3-minimal select.bp3-intent-danger .bp3-button-spinner .bp3-spinner-head, .bp3-select.bp3-minimal select.bp3-intent-danger .bp3-button-spinner .bp3-spinner-head{
        stroke:#c23030; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-danger, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-danger,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-danger, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-danger{
        color:#ff7373; }
        .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-danger:hover, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-danger:hover,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-danger:hover, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-danger:hover{
          background:rgba(219, 55, 55, 0.2);
          color:#ff7373; }
        .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-danger:active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-danger:active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-danger:active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-danger:active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-danger.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-danger.bp3-active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-danger.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-danger.bp3-active{
          background:rgba(219, 55, 55, 0.3);
          color:#ff7373; }
        .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-danger:disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-danger:disabled,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-danger:disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-danger:disabled, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-danger.bp3-disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-danger.bp3-disabled,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-danger.bp3-disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-danger.bp3-disabled{
          background:none;
          color:rgba(255, 115, 115, 0.5); }
          .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-danger:disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-danger:disabled.bp3-active,
          .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-danger:disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-danger:disabled.bp3-active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-danger.bp3-disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-danger.bp3-disabled.bp3-active,
          .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-danger.bp3-disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-danger.bp3-disabled.bp3-active{
            background:rgba(219, 55, 55, 0.3); }

  .bp3-html-select.bp3-large select,
  .bp3-select.bp3-large select{
    font-size:16px;
    height:40px;
    padding-right:35px; }

  .bp3-dark .bp3-html-select select, .bp3-dark .bp3-select select{
    background-color:#394b59;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.05)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.05), rgba(255, 255, 255, 0));
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
    color:#f5f8fa; }
    .bp3-dark .bp3-html-select select:hover, .bp3-dark .bp3-select select:hover, .bp3-dark .bp3-html-select select:active, .bp3-dark .bp3-select select:active, .bp3-dark .bp3-html-select select.bp3-active, .bp3-dark .bp3-select select.bp3-active{
      color:#f5f8fa; }
    .bp3-dark .bp3-html-select select:hover, .bp3-dark .bp3-select select:hover{
      background-color:#30404d;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-html-select select:active, .bp3-dark .bp3-select select:active, .bp3-dark .bp3-html-select select.bp3-active, .bp3-dark .bp3-select select.bp3-active{
      background-color:#202b33;
      background-image:none;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
    .bp3-dark .bp3-html-select select:disabled, .bp3-dark .bp3-select select:disabled, .bp3-dark .bp3-html-select select.bp3-disabled, .bp3-dark .bp3-select select.bp3-disabled{
      background-color:rgba(57, 75, 89, 0.5);
      background-image:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(167, 182, 194, 0.6); }
      .bp3-dark .bp3-html-select select:disabled.bp3-active, .bp3-dark .bp3-select select:disabled.bp3-active, .bp3-dark .bp3-html-select select.bp3-disabled.bp3-active, .bp3-dark .bp3-select select.bp3-disabled.bp3-active{
        background:rgba(57, 75, 89, 0.7); }
    .bp3-dark .bp3-html-select select .bp3-button-spinner .bp3-spinner-head, .bp3-dark .bp3-select select .bp3-button-spinner .bp3-spinner-head{
      background:rgba(16, 22, 26, 0.5);
      stroke:#8a9ba8; }

  .bp3-html-select select:disabled,
  .bp3-select select:disabled{
    background-color:rgba(206, 217, 224, 0.5);
    -webkit-box-shadow:none;
            box-shadow:none;
    color:rgba(92, 112, 128, 0.6);
    cursor:not-allowed; }

  .bp3-html-select .bp3-icon,
  .bp3-select .bp3-icon, .bp3-select::after{
    color:#5c7080;
    pointer-events:none;
    position:absolute;
    right:7px;
    top:7px; }
    .bp3-html-select .bp3-disabled.bp3-icon,
    .bp3-select .bp3-disabled.bp3-icon, .bp3-disabled.bp3-select::after{
      color:rgba(92, 112, 128, 0.6); }
  .bp3-html-select,
  .bp3-select{
    display:inline-block;
    letter-spacing:normal;
    position:relative;
    vertical-align:middle; }
    .bp3-html-select select::-ms-expand,
    .bp3-select select::-ms-expand{
      display:none; }
    .bp3-html-select .bp3-icon,
    .bp3-select .bp3-icon{
      color:#5c7080; }
      .bp3-html-select .bp3-icon:hover,
      .bp3-select .bp3-icon:hover{
        color:#182026; }
      .bp3-dark .bp3-html-select .bp3-icon, .bp3-dark
      .bp3-select .bp3-icon{
        color:#a7b6c2; }
        .bp3-dark .bp3-html-select .bp3-icon:hover, .bp3-dark
        .bp3-select .bp3-icon:hover{
          color:#f5f8fa; }
    .bp3-html-select.bp3-large::after,
    .bp3-html-select.bp3-large .bp3-icon,
    .bp3-select.bp3-large::after,
    .bp3-select.bp3-large .bp3-icon{
      right:12px;
      top:12px; }
    .bp3-html-select.bp3-fill,
    .bp3-html-select.bp3-fill select,
    .bp3-select.bp3-fill,
    .bp3-select.bp3-fill select{
      width:100%; }
    .bp3-dark .bp3-html-select option, .bp3-dark
    .bp3-select option{
      background-color:#30404d;
      color:#f5f8fa; }
    .bp3-dark .bp3-html-select option:disabled, .bp3-dark
    .bp3-select option:disabled{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-html-select::after, .bp3-dark
    .bp3-select::after{
      color:#a7b6c2; }

  .bp3-select::after{
    font-family:"Icons16", sans-serif;
    font-size:16px;
    font-style:normal;
    font-weight:400;
    line-height:1;
    -moz-osx-font-smoothing:grayscale;
    -webkit-font-smoothing:antialiased;
    content:""; }
  .bp3-running-text table, table.bp3-html-table{
    border-spacing:0;
    font-size:14px; }
    .bp3-running-text table th, table.bp3-html-table th,
    .bp3-running-text table td,
    table.bp3-html-table td{
      padding:11px;
      text-align:left;
      vertical-align:top; }
    .bp3-running-text table th, table.bp3-html-table th{
      color:#182026;
      font-weight:600; }
    
    .bp3-running-text table td,
    table.bp3-html-table td{
      color:#182026; }
    .bp3-running-text table tbody tr:first-child th, table.bp3-html-table tbody tr:first-child th,
    .bp3-running-text table tbody tr:first-child td,
    table.bp3-html-table tbody tr:first-child td{
      -webkit-box-shadow:inset 0 1px 0 0 rgba(16, 22, 26, 0.15);
              box-shadow:inset 0 1px 0 0 rgba(16, 22, 26, 0.15); }
    .bp3-dark .bp3-running-text table th, .bp3-running-text .bp3-dark table th, .bp3-dark table.bp3-html-table th{
      color:#f5f8fa; }
    .bp3-dark .bp3-running-text table td, .bp3-running-text .bp3-dark table td, .bp3-dark table.bp3-html-table td{
      color:#f5f8fa; }
    .bp3-dark .bp3-running-text table tbody tr:first-child th, .bp3-running-text .bp3-dark table tbody tr:first-child th, .bp3-dark table.bp3-html-table tbody tr:first-child th,
    .bp3-dark .bp3-running-text table tbody tr:first-child td,
    .bp3-running-text .bp3-dark table tbody tr:first-child td,
    .bp3-dark table.bp3-html-table tbody tr:first-child td{
      -webkit-box-shadow:inset 0 1px 0 0 rgba(255, 255, 255, 0.15);
              box-shadow:inset 0 1px 0 0 rgba(255, 255, 255, 0.15); }

  table.bp3-html-table.bp3-html-table-condensed th,
  table.bp3-html-table.bp3-html-table-condensed td, table.bp3-html-table.bp3-small th,
  table.bp3-html-table.bp3-small td{
    padding-bottom:6px;
    padding-top:6px; }

  table.bp3-html-table.bp3-html-table-striped tbody tr:nth-child(odd) td{
    background:rgba(191, 204, 214, 0.15); }

  table.bp3-html-table.bp3-html-table-bordered th:not(:first-child){
    -webkit-box-shadow:inset 1px 0 0 0 rgba(16, 22, 26, 0.15);
            box-shadow:inset 1px 0 0 0 rgba(16, 22, 26, 0.15); }

  table.bp3-html-table.bp3-html-table-bordered tbody tr td{
    -webkit-box-shadow:inset 0 1px 0 0 rgba(16, 22, 26, 0.15);
            box-shadow:inset 0 1px 0 0 rgba(16, 22, 26, 0.15); }
    table.bp3-html-table.bp3-html-table-bordered tbody tr td:not(:first-child){
      -webkit-box-shadow:inset 1px 1px 0 0 rgba(16, 22, 26, 0.15);
              box-shadow:inset 1px 1px 0 0 rgba(16, 22, 26, 0.15); }

  table.bp3-html-table.bp3-html-table-bordered.bp3-html-table-striped tbody tr:not(:first-child) td{
    -webkit-box-shadow:none;
            box-shadow:none; }
    table.bp3-html-table.bp3-html-table-bordered.bp3-html-table-striped tbody tr:not(:first-child) td:not(:first-child){
      -webkit-box-shadow:inset 1px 0 0 0 rgba(16, 22, 26, 0.15);
              box-shadow:inset 1px 0 0 0 rgba(16, 22, 26, 0.15); }

  table.bp3-html-table.bp3-interactive tbody tr:hover td{
    background-color:rgba(191, 204, 214, 0.3);
    cursor:pointer; }

  table.bp3-html-table.bp3-interactive tbody tr:active td{
    background-color:rgba(191, 204, 214, 0.4); }

  .bp3-dark table.bp3-html-table{ }
    .bp3-dark table.bp3-html-table.bp3-html-table-striped tbody tr:nth-child(odd) td{
      background:rgba(92, 112, 128, 0.15); }
    .bp3-dark table.bp3-html-table.bp3-html-table-bordered th:not(:first-child){
      -webkit-box-shadow:inset 1px 0 0 0 rgba(255, 255, 255, 0.15);
              box-shadow:inset 1px 0 0 0 rgba(255, 255, 255, 0.15); }
    .bp3-dark table.bp3-html-table.bp3-html-table-bordered tbody tr td{
      -webkit-box-shadow:inset 0 1px 0 0 rgba(255, 255, 255, 0.15);
              box-shadow:inset 0 1px 0 0 rgba(255, 255, 255, 0.15); }
      .bp3-dark table.bp3-html-table.bp3-html-table-bordered tbody tr td:not(:first-child){
        -webkit-box-shadow:inset 1px 1px 0 0 rgba(255, 255, 255, 0.15);
                box-shadow:inset 1px 1px 0 0 rgba(255, 255, 255, 0.15); }
    .bp3-dark table.bp3-html-table.bp3-html-table-bordered.bp3-html-table-striped tbody tr:not(:first-child) td{
      -webkit-box-shadow:inset 1px 0 0 0 rgba(255, 255, 255, 0.15);
              box-shadow:inset 1px 0 0 0 rgba(255, 255, 255, 0.15); }
      .bp3-dark table.bp3-html-table.bp3-html-table-bordered.bp3-html-table-striped tbody tr:not(:first-child) td:first-child{
        -webkit-box-shadow:none;
                box-shadow:none; }
    .bp3-dark table.bp3-html-table.bp3-interactive tbody tr:hover td{
      background-color:rgba(92, 112, 128, 0.3);
      cursor:pointer; }
    .bp3-dark table.bp3-html-table.bp3-interactive tbody tr:active td{
      background-color:rgba(92, 112, 128, 0.4); }

  .bp3-key-combo{
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    -webkit-box-orient:horizontal;
    -webkit-box-direction:normal;
        -ms-flex-direction:row;
            flex-direction:row;
    -webkit-box-align:center;
        -ms-flex-align:center;
            align-items:center; }
    .bp3-key-combo > *{
      -webkit-box-flex:0;
          -ms-flex-positive:0;
              flex-grow:0;
      -ms-flex-negative:0;
          flex-shrink:0; }
    .bp3-key-combo > .bp3-fill{
      -webkit-box-flex:1;
          -ms-flex-positive:1;
              flex-grow:1;
      -ms-flex-negative:1;
          flex-shrink:1; }
    .bp3-key-combo::before,
    .bp3-key-combo > *{
      margin-right:5px; }
    .bp3-key-combo:empty::before,
    .bp3-key-combo > :last-child{
      margin-right:0; }

  .bp3-hotkey-dialog{
    padding-bottom:0;
    top:40px; }
    .bp3-hotkey-dialog .bp3-dialog-body{
      margin:0;
      padding:0; }
    .bp3-hotkey-dialog .bp3-hotkey-label{
      -webkit-box-flex:1;
          -ms-flex-positive:1;
              flex-grow:1; }

  .bp3-hotkey-column{
    margin:auto;
    max-height:80vh;
    overflow-y:auto;
    padding:30px; }
    .bp3-hotkey-column .bp3-heading{
      margin-bottom:20px; }
      .bp3-hotkey-column .bp3-heading:not(:first-child){
        margin-top:40px; }

  .bp3-hotkey{
    -webkit-box-align:center;
        -ms-flex-align:center;
            align-items:center;
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    -webkit-box-pack:justify;
        -ms-flex-pack:justify;
            justify-content:space-between;
    margin-left:0;
    margin-right:0; }
    .bp3-hotkey:not(:last-child){
      margin-bottom:10px; }
  .bp3-icon{
    display:inline-block;
    -webkit-box-flex:0;
        -ms-flex:0 0 auto;
            flex:0 0 auto;
    vertical-align:text-bottom; }
    .bp3-icon:not(:empty)::before{
      content:"" !important;
      content:unset !important; }
    .bp3-icon > svg{
      display:block; }
      .bp3-icon > svg:not([fill]){
        fill:currentColor; }

  .bp3-icon.bp3-intent-primary, .bp3-icon-standard.bp3-intent-primary, .bp3-icon-large.bp3-intent-primary{
    color:#106ba3; }
    .bp3-dark .bp3-icon.bp3-intent-primary, .bp3-dark .bp3-icon-standard.bp3-intent-primary, .bp3-dark .bp3-icon-large.bp3-intent-primary{
      color:#48aff0; }

  .bp3-icon.bp3-intent-success, .bp3-icon-standard.bp3-intent-success, .bp3-icon-large.bp3-intent-success{
    color:#0d8050; }
    .bp3-dark .bp3-icon.bp3-intent-success, .bp3-dark .bp3-icon-standard.bp3-intent-success, .bp3-dark .bp3-icon-large.bp3-intent-success{
      color:#3dcc91; }

  .bp3-icon.bp3-intent-warning, .bp3-icon-standard.bp3-intent-warning, .bp3-icon-large.bp3-intent-warning{
    color:#bf7326; }
    .bp3-dark .bp3-icon.bp3-intent-warning, .bp3-dark .bp3-icon-standard.bp3-intent-warning, .bp3-dark .bp3-icon-large.bp3-intent-warning{
      color:#ffb366; }

  .bp3-icon.bp3-intent-danger, .bp3-icon-standard.bp3-intent-danger, .bp3-icon-large.bp3-intent-danger{
    color:#c23030; }
    .bp3-dark .bp3-icon.bp3-intent-danger, .bp3-dark .bp3-icon-standard.bp3-intent-danger, .bp3-dark .bp3-icon-large.bp3-intent-danger{
      color:#ff7373; }

  span.bp3-icon-standard{
    font-family:"Icons16", sans-serif;
    font-size:16px;
    font-style:normal;
    font-weight:400;
    line-height:1;
    -moz-osx-font-smoothing:grayscale;
    -webkit-font-smoothing:antialiased;
    display:inline-block; }

  span.bp3-icon-large{
    font-family:"Icons20", sans-serif;
    font-size:20px;
    font-style:normal;
    font-weight:400;
    line-height:1;
    -moz-osx-font-smoothing:grayscale;
    -webkit-font-smoothing:antialiased;
    display:inline-block; }

  span.bp3-icon:empty{
    font-family:"Icons20";
    font-size:inherit;
    font-style:normal;
    font-weight:400;
    line-height:1; }
    span.bp3-icon:empty::before{
      -moz-osx-font-smoothing:grayscale;
      -webkit-font-smoothing:antialiased; }

  .bp3-icon-add::before{
    content:""; }

  .bp3-icon-add-column-left::before{
    content:""; }

  .bp3-icon-add-column-right::before{
    content:""; }

  .bp3-icon-add-row-bottom::before{
    content:""; }

  .bp3-icon-add-row-top::before{
    content:""; }

  .bp3-icon-add-to-artifact::before{
    content:""; }

  .bp3-icon-add-to-folder::before{
    content:""; }

  .bp3-icon-airplane::before{
    content:""; }

  .bp3-icon-align-center::before{
    content:""; }

  .bp3-icon-align-justify::before{
    content:""; }

  .bp3-icon-align-left::before{
    content:""; }

  .bp3-icon-align-right::before{
    content:""; }

  .bp3-icon-alignment-bottom::before{
    content:""; }

  .bp3-icon-alignment-horizontal-center::before{
    content:""; }

  .bp3-icon-alignment-left::before{
    content:""; }

  .bp3-icon-alignment-right::before{
    content:""; }

  .bp3-icon-alignment-top::before{
    content:""; }

  .bp3-icon-alignment-vertical-center::before{
    content:""; }

  .bp3-icon-annotation::before{
    content:""; }

  .bp3-icon-application::before{
    content:""; }

  .bp3-icon-applications::before{
    content:""; }

  .bp3-icon-archive::before{
    content:""; }

  .bp3-icon-arrow-bottom-left::before{
    content:"↙"; }

  .bp3-icon-arrow-bottom-right::before{
    content:"↘"; }

  .bp3-icon-arrow-down::before{
    content:"↓"; }

  .bp3-icon-arrow-left::before{
    content:"←"; }

  .bp3-icon-arrow-right::before{
    content:"→"; }

  .bp3-icon-arrow-top-left::before{
    content:"↖"; }

  .bp3-icon-arrow-top-right::before{
    content:"↗"; }

  .bp3-icon-arrow-up::before{
    content:"↑"; }

  .bp3-icon-arrows-horizontal::before{
    content:"↔"; }

  .bp3-icon-arrows-vertical::before{
    content:"↕"; }

  .bp3-icon-asterisk::before{
    content:"*"; }

  .bp3-icon-automatic-updates::before{
    content:""; }

  .bp3-icon-badge::before{
    content:""; }

  .bp3-icon-ban-circle::before{
    content:""; }

  .bp3-icon-bank-account::before{
    content:""; }

  .bp3-icon-barcode::before{
    content:""; }

  .bp3-icon-blank::before{
    content:""; }

  .bp3-icon-blocked-person::before{
    content:""; }

  .bp3-icon-bold::before{
    content:""; }

  .bp3-icon-book::before{
    content:""; }

  .bp3-icon-bookmark::before{
    content:""; }

  .bp3-icon-box::before{
    content:""; }

  .bp3-icon-briefcase::before{
    content:""; }

  .bp3-icon-bring-data::before{
    content:""; }

  .bp3-icon-build::before{
    content:""; }

  .bp3-icon-calculator::before{
    content:""; }

  .bp3-icon-calendar::before{
    content:""; }

  .bp3-icon-camera::before{
    content:""; }

  .bp3-icon-caret-down::before{
    content:"⌄"; }

  .bp3-icon-caret-left::before{
    content:"〈"; }

  .bp3-icon-caret-right::before{
    content:"〉"; }

  .bp3-icon-caret-up::before{
    content:"⌃"; }

  .bp3-icon-cell-tower::before{
    content:""; }

  .bp3-icon-changes::before{
    content:""; }

  .bp3-icon-chart::before{
    content:""; }

  .bp3-icon-chat::before{
    content:""; }

  .bp3-icon-chevron-backward::before{
    content:""; }

  .bp3-icon-chevron-down::before{
    content:""; }

  .bp3-icon-chevron-forward::before{
    content:""; }

  .bp3-icon-chevron-left::before{
    content:""; }

  .bp3-icon-chevron-right::before{
    content:""; }

  .bp3-icon-chevron-up::before{
    content:""; }

  .bp3-icon-circle::before{
    content:""; }

  .bp3-icon-circle-arrow-down::before{
    content:""; }

  .bp3-icon-circle-arrow-left::before{
    content:""; }

  .bp3-icon-circle-arrow-right::before{
    content:""; }

  .bp3-icon-circle-arrow-up::before{
    content:""; }

  .bp3-icon-citation::before{
    content:""; }

  .bp3-icon-clean::before{
    content:""; }

  .bp3-icon-clipboard::before{
    content:""; }

  .bp3-icon-cloud::before{
    content:"☁"; }

  .bp3-icon-cloud-download::before{
    content:""; }

  .bp3-icon-cloud-upload::before{
    content:""; }

  .bp3-icon-code::before{
    content:""; }

  .bp3-icon-code-block::before{
    content:""; }

  .bp3-icon-cog::before{
    content:""; }

  .bp3-icon-collapse-all::before{
    content:""; }

  .bp3-icon-column-layout::before{
    content:""; }

  .bp3-icon-comment::before{
    content:""; }

  .bp3-icon-comparison::before{
    content:""; }

  .bp3-icon-compass::before{
    content:""; }

  .bp3-icon-compressed::before{
    content:""; }

  .bp3-icon-confirm::before{
    content:""; }

  .bp3-icon-console::before{
    content:""; }

  .bp3-icon-contrast::before{
    content:""; }

  .bp3-icon-control::before{
    content:""; }

  .bp3-icon-credit-card::before{
    content:""; }

  .bp3-icon-cross::before{
    content:"✗"; }

  .bp3-icon-crown::before{
    content:""; }

  .bp3-icon-cube::before{
    content:""; }

  .bp3-icon-cube-add::before{
    content:""; }

  .bp3-icon-cube-remove::before{
    content:""; }

  .bp3-icon-curved-range-chart::before{
    content:""; }

  .bp3-icon-cut::before{
    content:""; }

  .bp3-icon-dashboard::before{
    content:""; }

  .bp3-icon-data-lineage::before{
    content:""; }

  .bp3-icon-database::before{
    content:""; }

  .bp3-icon-delete::before{
    content:""; }

  .bp3-icon-delta::before{
    content:"Δ"; }

  .bp3-icon-derive-column::before{
    content:""; }

  .bp3-icon-desktop::before{
    content:""; }

  .bp3-icon-diagnosis::before{
    content:""; }

  .bp3-icon-diagram-tree::before{
    content:""; }

  .bp3-icon-direction-left::before{
    content:""; }

  .bp3-icon-direction-right::before{
    content:""; }

  .bp3-icon-disable::before{
    content:""; }

  .bp3-icon-document::before{
    content:""; }

  .bp3-icon-document-open::before{
    content:""; }

  .bp3-icon-document-share::before{
    content:""; }

  .bp3-icon-dollar::before{
    content:"$"; }

  .bp3-icon-dot::before{
    content:"•"; }

  .bp3-icon-double-caret-horizontal::before{
    content:""; }

  .bp3-icon-double-caret-vertical::before{
    content:""; }

  .bp3-icon-double-chevron-down::before{
    content:""; }

  .bp3-icon-double-chevron-left::before{
    content:""; }

  .bp3-icon-double-chevron-right::before{
    content:""; }

  .bp3-icon-double-chevron-up::before{
    content:""; }

  .bp3-icon-doughnut-chart::before{
    content:""; }

  .bp3-icon-download::before{
    content:""; }

  .bp3-icon-drag-handle-horizontal::before{
    content:""; }

  .bp3-icon-drag-handle-vertical::before{
    content:""; }

  .bp3-icon-draw::before{
    content:""; }

  .bp3-icon-drive-time::before{
    content:""; }

  .bp3-icon-duplicate::before{
    content:""; }

  .bp3-icon-edit::before{
    content:"✎"; }

  .bp3-icon-eject::before{
    content:"⏏"; }

  .bp3-icon-endorsed::before{
    content:""; }

  .bp3-icon-envelope::before{
    content:"✉"; }

  .bp3-icon-equals::before{
    content:""; }

  .bp3-icon-eraser::before{
    content:""; }

  .bp3-icon-error::before{
    content:""; }

  .bp3-icon-euro::before{
    content:"€"; }

  .bp3-icon-exchange::before{
    content:""; }

  .bp3-icon-exclude-row::before{
    content:""; }

  .bp3-icon-expand-all::before{
    content:""; }

  .bp3-icon-export::before{
    content:""; }

  .bp3-icon-eye-off::before{
    content:""; }

  .bp3-icon-eye-on::before{
    content:""; }

  .bp3-icon-eye-open::before{
    content:""; }

  .bp3-icon-fast-backward::before{
    content:""; }

  .bp3-icon-fast-forward::before{
    content:""; }

  .bp3-icon-feed::before{
    content:""; }

  .bp3-icon-feed-subscribed::before{
    content:""; }

  .bp3-icon-film::before{
    content:""; }

  .bp3-icon-filter::before{
    content:""; }

  .bp3-icon-filter-keep::before{
    content:""; }

  .bp3-icon-filter-list::before{
    content:""; }

  .bp3-icon-filter-open::before{
    content:""; }

  .bp3-icon-filter-remove::before{
    content:""; }

  .bp3-icon-flag::before{
    content:"⚑"; }

  .bp3-icon-flame::before{
    content:""; }

  .bp3-icon-flash::before{
    content:""; }

  .bp3-icon-floppy-disk::before{
    content:""; }

  .bp3-icon-flow-branch::before{
    content:""; }

  .bp3-icon-flow-end::before{
    content:""; }

  .bp3-icon-flow-linear::before{
    content:""; }

  .bp3-icon-flow-review::before{
    content:""; }

  .bp3-icon-flow-review-branch::before{
    content:""; }

  .bp3-icon-flows::before{
    content:""; }

  .bp3-icon-folder-close::before{
    content:""; }

  .bp3-icon-folder-new::before{
    content:""; }

  .bp3-icon-folder-open::before{
    content:""; }

  .bp3-icon-folder-shared::before{
    content:""; }

  .bp3-icon-folder-shared-open::before{
    content:""; }

  .bp3-icon-follower::before{
    content:""; }

  .bp3-icon-following::before{
    content:""; }

  .bp3-icon-font::before{
    content:""; }

  .bp3-icon-fork::before{
    content:""; }

  .bp3-icon-form::before{
    content:""; }

  .bp3-icon-full-circle::before{
    content:""; }

  .bp3-icon-full-stacked-chart::before{
    content:""; }

  .bp3-icon-fullscreen::before{
    content:""; }

  .bp3-icon-function::before{
    content:""; }

  .bp3-icon-gantt-chart::before{
    content:""; }

  .bp3-icon-geolocation::before{
    content:""; }

  .bp3-icon-geosearch::before{
    content:""; }

  .bp3-icon-git-branch::before{
    content:""; }

  .bp3-icon-git-commit::before{
    content:""; }

  .bp3-icon-git-merge::before{
    content:""; }

  .bp3-icon-git-new-branch::before{
    content:""; }

  .bp3-icon-git-pull::before{
    content:""; }

  .bp3-icon-git-push::before{
    content:""; }

  .bp3-icon-git-repo::before{
    content:""; }

  .bp3-icon-glass::before{
    content:""; }

  .bp3-icon-globe::before{
    content:""; }

  .bp3-icon-globe-network::before{
    content:""; }

  .bp3-icon-graph::before{
    content:""; }

  .bp3-icon-graph-remove::before{
    content:""; }

  .bp3-icon-greater-than::before{
    content:""; }

  .bp3-icon-greater-than-or-equal-to::before{
    content:""; }

  .bp3-icon-grid::before{
    content:""; }

  .bp3-icon-grid-view::before{
    content:""; }

  .bp3-icon-group-objects::before{
    content:""; }

  .bp3-icon-grouped-bar-chart::before{
    content:""; }

  .bp3-icon-hand::before{
    content:""; }

  .bp3-icon-hand-down::before{
    content:""; }

  .bp3-icon-hand-left::before{
    content:""; }

  .bp3-icon-hand-right::before{
    content:""; }

  .bp3-icon-hand-up::before{
    content:""; }

  .bp3-icon-header::before{
    content:""; }

  .bp3-icon-header-one::before{
    content:""; }

  .bp3-icon-header-two::before{
    content:""; }

  .bp3-icon-headset::before{
    content:""; }

  .bp3-icon-heart::before{
    content:"♥"; }

  .bp3-icon-heart-broken::before{
    content:""; }

  .bp3-icon-heat-grid::before{
    content:""; }

  .bp3-icon-heatmap::before{
    content:""; }

  .bp3-icon-help::before{
    content:"?"; }

  .bp3-icon-helper-management::before{
    content:""; }

  .bp3-icon-highlight::before{
    content:""; }

  .bp3-icon-history::before{
    content:""; }

  .bp3-icon-home::before{
    content:"⌂"; }

  .bp3-icon-horizontal-bar-chart::before{
    content:""; }

  .bp3-icon-horizontal-bar-chart-asc::before{
    content:""; }

  .bp3-icon-horizontal-bar-chart-desc::before{
    content:""; }

  .bp3-icon-horizontal-distribution::before{
    content:""; }

  .bp3-icon-id-number::before{
    content:""; }

  .bp3-icon-image-rotate-left::before{
    content:""; }

  .bp3-icon-image-rotate-right::before{
    content:""; }

  .bp3-icon-import::before{
    content:""; }

  .bp3-icon-inbox::before{
    content:""; }

  .bp3-icon-inbox-filtered::before{
    content:""; }

  .bp3-icon-inbox-geo::before{
    content:""; }

  .bp3-icon-inbox-search::before{
    content:""; }

  .bp3-icon-inbox-update::before{
    content:""; }

  .bp3-icon-info-sign::before{
    content:"ℹ"; }

  .bp3-icon-inheritance::before{
    content:""; }

  .bp3-icon-inner-join::before{
    content:""; }

  .bp3-icon-insert::before{
    content:""; }

  .bp3-icon-intersection::before{
    content:""; }

  .bp3-icon-ip-address::before{
    content:""; }

  .bp3-icon-issue::before{
    content:""; }

  .bp3-icon-issue-closed::before{
    content:""; }

  .bp3-icon-issue-new::before{
    content:""; }

  .bp3-icon-italic::before{
    content:""; }

  .bp3-icon-join-table::before{
    content:""; }

  .bp3-icon-key::before{
    content:""; }

  .bp3-icon-key-backspace::before{
    content:""; }

  .bp3-icon-key-command::before{
    content:""; }

  .bp3-icon-key-control::before{
    content:""; }

  .bp3-icon-key-delete::before{
    content:""; }

  .bp3-icon-key-enter::before{
    content:""; }

  .bp3-icon-key-escape::before{
    content:""; }

  .bp3-icon-key-option::before{
    content:""; }

  .bp3-icon-key-shift::before{
    content:""; }

  .bp3-icon-key-tab::before{
    content:""; }

  .bp3-icon-known-vehicle::before{
    content:""; }

  .bp3-icon-lab-test::before{
    content:""; }

  .bp3-icon-label::before{
    content:""; }

  .bp3-icon-layer::before{
    content:""; }

  .bp3-icon-layers::before{
    content:""; }

  .bp3-icon-layout::before{
    content:""; }

  .bp3-icon-layout-auto::before{
    content:""; }

  .bp3-icon-layout-balloon::before{
    content:""; }

  .bp3-icon-layout-circle::before{
    content:""; }

  .bp3-icon-layout-grid::before{
    content:""; }

  .bp3-icon-layout-group-by::before{
    content:""; }

  .bp3-icon-layout-hierarchy::before{
    content:""; }

  .bp3-icon-layout-linear::before{
    content:""; }

  .bp3-icon-layout-skew-grid::before{
    content:""; }

  .bp3-icon-layout-sorted-clusters::before{
    content:""; }

  .bp3-icon-learning::before{
    content:""; }

  .bp3-icon-left-join::before{
    content:""; }

  .bp3-icon-less-than::before{
    content:""; }

  .bp3-icon-less-than-or-equal-to::before{
    content:""; }

  .bp3-icon-lifesaver::before{
    content:""; }

  .bp3-icon-lightbulb::before{
    content:""; }

  .bp3-icon-link::before{
    content:""; }

  .bp3-icon-list::before{
    content:"☰"; }

  .bp3-icon-list-columns::before{
    content:""; }

  .bp3-icon-list-detail-view::before{
    content:""; }

  .bp3-icon-locate::before{
    content:""; }

  .bp3-icon-lock::before{
    content:""; }

  .bp3-icon-log-in::before{
    content:""; }

  .bp3-icon-log-out::before{
    content:""; }

  .bp3-icon-manual::before{
    content:""; }

  .bp3-icon-manually-entered-data::before{
    content:""; }

  .bp3-icon-map::before{
    content:""; }

  .bp3-icon-map-create::before{
    content:""; }

  .bp3-icon-map-marker::before{
    content:""; }

  .bp3-icon-maximize::before{
    content:""; }

  .bp3-icon-media::before{
    content:""; }

  .bp3-icon-menu::before{
    content:""; }

  .bp3-icon-menu-closed::before{
    content:""; }

  .bp3-icon-menu-open::before{
    content:""; }

  .bp3-icon-merge-columns::before{
    content:""; }

  .bp3-icon-merge-links::before{
    content:""; }

  .bp3-icon-minimize::before{
    content:""; }

  .bp3-icon-minus::before{
    content:"−"; }

  .bp3-icon-mobile-phone::before{
    content:""; }

  .bp3-icon-mobile-video::before{
    content:""; }

  .bp3-icon-moon::before{
    content:""; }

  .bp3-icon-more::before{
    content:""; }

  .bp3-icon-mountain::before{
    content:""; }

  .bp3-icon-move::before{
    content:""; }

  .bp3-icon-mugshot::before{
    content:""; }

  .bp3-icon-multi-select::before{
    content:""; }

  .bp3-icon-music::before{
    content:""; }

  .bp3-icon-new-drawing::before{
    content:""; }

  .bp3-icon-new-grid-item::before{
    content:""; }

  .bp3-icon-new-layer::before{
    content:""; }

  .bp3-icon-new-layers::before{
    content:""; }

  .bp3-icon-new-link::before{
    content:""; }

  .bp3-icon-new-object::before{
    content:""; }

  .bp3-icon-new-person::before{
    content:""; }

  .bp3-icon-new-prescription::before{
    content:""; }

  .bp3-icon-new-text-box::before{
    content:""; }

  .bp3-icon-ninja::before{
    content:""; }

  .bp3-icon-not-equal-to::before{
    content:""; }

  .bp3-icon-notifications::before{
    content:""; }

  .bp3-icon-notifications-updated::before{
    content:""; }

  .bp3-icon-numbered-list::before{
    content:""; }

  .bp3-icon-numerical::before{
    content:""; }

  .bp3-icon-office::before{
    content:""; }

  .bp3-icon-offline::before{
    content:""; }

  .bp3-icon-oil-field::before{
    content:""; }

  .bp3-icon-one-column::before{
    content:""; }

  .bp3-icon-outdated::before{
    content:""; }

  .bp3-icon-page-layout::before{
    content:""; }

  .bp3-icon-panel-stats::before{
    content:""; }

  .bp3-icon-panel-table::before{
    content:""; }

  .bp3-icon-paperclip::before{
    content:""; }

  .bp3-icon-paragraph::before{
    content:""; }

  .bp3-icon-path::before{
    content:""; }

  .bp3-icon-path-search::before{
    content:""; }

  .bp3-icon-pause::before{
    content:""; }

  .bp3-icon-people::before{
    content:""; }

  .bp3-icon-percentage::before{
    content:""; }

  .bp3-icon-person::before{
    content:""; }

  .bp3-icon-phone::before{
    content:"☎"; }

  .bp3-icon-pie-chart::before{
    content:""; }

  .bp3-icon-pin::before{
    content:""; }

  .bp3-icon-pivot::before{
    content:""; }

  .bp3-icon-pivot-table::before{
    content:""; }

  .bp3-icon-play::before{
    content:""; }

  .bp3-icon-plus::before{
    content:"+"; }

  .bp3-icon-polygon-filter::before{
    content:""; }

  .bp3-icon-power::before{
    content:""; }

  .bp3-icon-predictive-analysis::before{
    content:""; }

  .bp3-icon-prescription::before{
    content:""; }

  .bp3-icon-presentation::before{
    content:""; }

  .bp3-icon-print::before{
    content:"⎙"; }

  .bp3-icon-projects::before{
    content:""; }

  .bp3-icon-properties::before{
    content:""; }

  .bp3-icon-property::before{
    content:""; }

  .bp3-icon-publish-function::before{
    content:""; }

  .bp3-icon-pulse::before{
    content:""; }

  .bp3-icon-random::before{
    content:""; }

  .bp3-icon-record::before{
    content:""; }

  .bp3-icon-redo::before{
    content:""; }

  .bp3-icon-refresh::before{
    content:""; }

  .bp3-icon-regression-chart::before{
    content:""; }

  .bp3-icon-remove::before{
    content:""; }

  .bp3-icon-remove-column::before{
    content:""; }

  .bp3-icon-remove-column-left::before{
    content:""; }

  .bp3-icon-remove-column-right::before{
    content:""; }

  .bp3-icon-remove-row-bottom::before{
    content:""; }

  .bp3-icon-remove-row-top::before{
    content:""; }

  .bp3-icon-repeat::before{
    content:""; }

  .bp3-icon-reset::before{
    content:""; }

  .bp3-icon-resolve::before{
    content:""; }

  .bp3-icon-rig::before{
    content:""; }

  .bp3-icon-right-join::before{
    content:""; }

  .bp3-icon-ring::before{
    content:""; }

  .bp3-icon-rotate-document::before{
    content:""; }

  .bp3-icon-rotate-page::before{
    content:""; }

  .bp3-icon-satellite::before{
    content:""; }

  .bp3-icon-saved::before{
    content:""; }

  .bp3-icon-scatter-plot::before{
    content:""; }

  .bp3-icon-search::before{
    content:""; }

  .bp3-icon-search-around::before{
    content:""; }

  .bp3-icon-search-template::before{
    content:""; }

  .bp3-icon-search-text::before{
    content:""; }

  .bp3-icon-segmented-control::before{
    content:""; }

  .bp3-icon-select::before{
    content:""; }

  .bp3-icon-selection::before{
    content:"⦿"; }

  .bp3-icon-send-to::before{
    content:""; }

  .bp3-icon-send-to-graph::before{
    content:""; }

  .bp3-icon-send-to-map::before{
    content:""; }

  .bp3-icon-series-add::before{
    content:""; }

  .bp3-icon-series-configuration::before{
    content:""; }

  .bp3-icon-series-derived::before{
    content:""; }

  .bp3-icon-series-filtered::before{
    content:""; }

  .bp3-icon-series-search::before{
    content:""; }

  .bp3-icon-settings::before{
    content:""; }

  .bp3-icon-share::before{
    content:""; }

  .bp3-icon-shield::before{
    content:""; }

  .bp3-icon-shop::before{
    content:""; }

  .bp3-icon-shopping-cart::before{
    content:""; }

  .bp3-icon-signal-search::before{
    content:""; }

  .bp3-icon-sim-card::before{
    content:""; }

  .bp3-icon-slash::before{
    content:""; }

  .bp3-icon-small-cross::before{
    content:""; }

  .bp3-icon-small-minus::before{
    content:""; }

  .bp3-icon-small-plus::before{
    content:""; }

  .bp3-icon-small-tick::before{
    content:""; }

  .bp3-icon-snowflake::before{
    content:""; }

  .bp3-icon-social-media::before{
    content:""; }

  .bp3-icon-sort::before{
    content:""; }

  .bp3-icon-sort-alphabetical::before{
    content:""; }

  .bp3-icon-sort-alphabetical-desc::before{
    content:""; }

  .bp3-icon-sort-asc::before{
    content:""; }

  .bp3-icon-sort-desc::before{
    content:""; }

  .bp3-icon-sort-numerical::before{
    content:""; }

  .bp3-icon-sort-numerical-desc::before{
    content:""; }

  .bp3-icon-split-columns::before{
    content:""; }

  .bp3-icon-square::before{
    content:""; }

  .bp3-icon-stacked-chart::before{
    content:""; }

  .bp3-icon-star::before{
    content:"★"; }

  .bp3-icon-star-empty::before{
    content:"☆"; }

  .bp3-icon-step-backward::before{
    content:""; }

  .bp3-icon-step-chart::before{
    content:""; }

  .bp3-icon-step-forward::before{
    content:""; }

  .bp3-icon-stop::before{
    content:""; }

  .bp3-icon-stopwatch::before{
    content:""; }

  .bp3-icon-strikethrough::before{
    content:""; }

  .bp3-icon-style::before{
    content:""; }

  .bp3-icon-swap-horizontal::before{
    content:""; }

  .bp3-icon-swap-vertical::before{
    content:""; }

  .bp3-icon-symbol-circle::before{
    content:""; }

  .bp3-icon-symbol-cross::before{
    content:""; }

  .bp3-icon-symbol-diamond::before{
    content:""; }

  .bp3-icon-symbol-square::before{
    content:""; }

  .bp3-icon-symbol-triangle-down::before{
    content:""; }

  .bp3-icon-symbol-triangle-up::before{
    content:""; }

  .bp3-icon-tag::before{
    content:""; }

  .bp3-icon-take-action::before{
    content:""; }

  .bp3-icon-taxi::before{
    content:""; }

  .bp3-icon-text-highlight::before{
    content:""; }

  .bp3-icon-th::before{
    content:""; }

  .bp3-icon-th-derived::before{
    content:""; }

  .bp3-icon-th-disconnect::before{
    content:""; }

  .bp3-icon-th-filtered::before{
    content:""; }

  .bp3-icon-th-list::before{
    content:""; }

  .bp3-icon-thumbs-down::before{
    content:""; }

  .bp3-icon-thumbs-up::before{
    content:""; }

  .bp3-icon-tick::before{
    content:"✓"; }

  .bp3-icon-tick-circle::before{
    content:""; }

  .bp3-icon-time::before{
    content:"⏲"; }

  .bp3-icon-timeline-area-chart::before{
    content:""; }

  .bp3-icon-timeline-bar-chart::before{
    content:""; }

  .bp3-icon-timeline-events::before{
    content:""; }

  .bp3-icon-timeline-line-chart::before{
    content:""; }

  .bp3-icon-tint::before{
    content:""; }

  .bp3-icon-torch::before{
    content:""; }

  .bp3-icon-tractor::before{
    content:""; }

  .bp3-icon-train::before{
    content:""; }

  .bp3-icon-translate::before{
    content:""; }

  .bp3-icon-trash::before{
    content:""; }

  .bp3-icon-tree::before{
    content:""; }

  .bp3-icon-trending-down::before{
    content:""; }

  .bp3-icon-trending-up::before{
    content:""; }

  .bp3-icon-truck::before{
    content:""; }

  .bp3-icon-two-columns::before{
    content:""; }

  .bp3-icon-unarchive::before{
    content:""; }

  .bp3-icon-underline::before{
    content:"⎁"; }

  .bp3-icon-undo::before{
    content:"⎌"; }

  .bp3-icon-ungroup-objects::before{
    content:""; }

  .bp3-icon-unknown-vehicle::before{
    content:""; }

  .bp3-icon-unlock::before{
    content:""; }

  .bp3-icon-unpin::before{
    content:""; }

  .bp3-icon-unresolve::before{
    content:""; }

  .bp3-icon-updated::before{
    content:""; }

  .bp3-icon-upload::before{
    content:""; }

  .bp3-icon-user::before{
    content:""; }

  .bp3-icon-variable::before{
    content:""; }

  .bp3-icon-vertical-bar-chart-asc::before{
    content:""; }

  .bp3-icon-vertical-bar-chart-desc::before{
    content:""; }

  .bp3-icon-vertical-distribution::before{
    content:""; }

  .bp3-icon-video::before{
    content:""; }

  .bp3-icon-volume-down::before{
    content:""; }

  .bp3-icon-volume-off::before{
    content:""; }

  .bp3-icon-volume-up::before{
    content:""; }

  .bp3-icon-walk::before{
    content:""; }

  .bp3-icon-warning-sign::before{
    content:""; }

  .bp3-icon-waterfall-chart::before{
    content:""; }

  .bp3-icon-widget::before{
    content:""; }

  .bp3-icon-widget-button::before{
    content:""; }

  .bp3-icon-widget-footer::before{
    content:""; }

  .bp3-icon-widget-header::before{
    content:""; }

  .bp3-icon-wrench::before{
    content:""; }

  .bp3-icon-zoom-in::before{
    content:""; }

  .bp3-icon-zoom-out::before{
    content:""; }

  .bp3-icon-zoom-to-fit::before{
    content:""; }
  .bp3-submenu > .bp3-popover-wrapper{
    display:block; }

  .bp3-submenu .bp3-popover-target{
    display:block; }
    .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-menu-item{ }

  .bp3-submenu.bp3-popover{
    -webkit-box-shadow:none;
            box-shadow:none;
    padding:0 5px; }
    .bp3-submenu.bp3-popover > .bp3-popover-content{
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2); }
    .bp3-dark .bp3-submenu.bp3-popover, .bp3-submenu.bp3-popover.bp3-dark{
      -webkit-box-shadow:none;
              box-shadow:none; }
      .bp3-dark .bp3-submenu.bp3-popover > .bp3-popover-content, .bp3-submenu.bp3-popover.bp3-dark > .bp3-popover-content{
        -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
                box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4); }
  .bp3-menu{
    background:#ffffff;
    border-radius:3px;
    color:#182026;
    list-style:none;
    margin:0;
    min-width:180px;
    padding:5px;
    text-align:left; }

  .bp3-menu-divider{
    border-top:1px solid rgba(16, 22, 26, 0.15);
    display:block;
    margin:5px; }
    .bp3-dark .bp3-menu-divider{
      border-top-color:rgba(255, 255, 255, 0.15); }

  .bp3-menu-item{
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    -webkit-box-orient:horizontal;
    -webkit-box-direction:normal;
        -ms-flex-direction:row;
            flex-direction:row;
    -webkit-box-align:start;
        -ms-flex-align:start;
            align-items:flex-start;
    border-radius:2px;
    color:inherit;
    line-height:20px;
    padding:5px 7px;
    text-decoration:none;
    -webkit-user-select:none;
      -moz-user-select:none;
        -ms-user-select:none;
            user-select:none; }
    .bp3-menu-item > *{
      -webkit-box-flex:0;
          -ms-flex-positive:0;
              flex-grow:0;
      -ms-flex-negative:0;
          flex-shrink:0; }
    .bp3-menu-item > .bp3-fill{
      -webkit-box-flex:1;
          -ms-flex-positive:1;
              flex-grow:1;
      -ms-flex-negative:1;
          flex-shrink:1; }
    .bp3-menu-item::before,
    .bp3-menu-item > *{
      margin-right:7px; }
    .bp3-menu-item:empty::before,
    .bp3-menu-item > :last-child{
      margin-right:0; }
    .bp3-menu-item > .bp3-fill{
      word-break:break-word; }
    .bp3-menu-item:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-menu-item{
      background-color:rgba(167, 182, 194, 0.3);
      cursor:pointer;
      text-decoration:none; }
    .bp3-menu-item.bp3-disabled{
      background-color:inherit;
      color:rgba(92, 112, 128, 0.6);
      cursor:not-allowed; }
    .bp3-dark .bp3-menu-item{
      color:inherit; }
      .bp3-dark .bp3-menu-item:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-menu-item{
        background-color:rgba(138, 155, 168, 0.15);
        color:inherit; }
      .bp3-dark .bp3-menu-item.bp3-disabled{
        background-color:inherit;
        color:rgba(167, 182, 194, 0.6); }
    .bp3-menu-item.bp3-intent-primary{
      color:#106ba3; }
      .bp3-menu-item.bp3-intent-primary .bp3-icon{
        color:inherit; }
      .bp3-menu-item.bp3-intent-primary::before, .bp3-menu-item.bp3-intent-primary::after,
      .bp3-menu-item.bp3-intent-primary .bp3-menu-item-label{
        color:#106ba3; }
      .bp3-menu-item.bp3-intent-primary:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item, .bp3-menu-item.bp3-intent-primary.bp3-active{
        background-color:#137cbd; }
      .bp3-menu-item.bp3-intent-primary:active{
        background-color:#106ba3; }
      .bp3-menu-item.bp3-intent-primary:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item, .bp3-menu-item.bp3-intent-primary:hover::before, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item::before, .bp3-menu-item.bp3-intent-primary:hover::after, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item::after,
      .bp3-menu-item.bp3-intent-primary:hover .bp3-menu-item-label,
      .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item .bp3-menu-item-label, .bp3-menu-item.bp3-intent-primary:active, .bp3-menu-item.bp3-intent-primary:active::before, .bp3-menu-item.bp3-intent-primary:active::after,
      .bp3-menu-item.bp3-intent-primary:active .bp3-menu-item-label, .bp3-menu-item.bp3-intent-primary.bp3-active, .bp3-menu-item.bp3-intent-primary.bp3-active::before, .bp3-menu-item.bp3-intent-primary.bp3-active::after,
      .bp3-menu-item.bp3-intent-primary.bp3-active .bp3-menu-item-label{
        color:#ffffff; }
    .bp3-menu-item.bp3-intent-success{
      color:#0d8050; }
      .bp3-menu-item.bp3-intent-success .bp3-icon{
        color:inherit; }
      .bp3-menu-item.bp3-intent-success::before, .bp3-menu-item.bp3-intent-success::after,
      .bp3-menu-item.bp3-intent-success .bp3-menu-item-label{
        color:#0d8050; }
      .bp3-menu-item.bp3-intent-success:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item, .bp3-menu-item.bp3-intent-success.bp3-active{
        background-color:#0f9960; }
      .bp3-menu-item.bp3-intent-success:active{
        background-color:#0d8050; }
      .bp3-menu-item.bp3-intent-success:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item, .bp3-menu-item.bp3-intent-success:hover::before, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item::before, .bp3-menu-item.bp3-intent-success:hover::after, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item::after,
      .bp3-menu-item.bp3-intent-success:hover .bp3-menu-item-label,
      .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item .bp3-menu-item-label, .bp3-menu-item.bp3-intent-success:active, .bp3-menu-item.bp3-intent-success:active::before, .bp3-menu-item.bp3-intent-success:active::after,
      .bp3-menu-item.bp3-intent-success:active .bp3-menu-item-label, .bp3-menu-item.bp3-intent-success.bp3-active, .bp3-menu-item.bp3-intent-success.bp3-active::before, .bp3-menu-item.bp3-intent-success.bp3-active::after,
      .bp3-menu-item.bp3-intent-success.bp3-active .bp3-menu-item-label{
        color:#ffffff; }
    .bp3-menu-item.bp3-intent-warning{
      color:#bf7326; }
      .bp3-menu-item.bp3-intent-warning .bp3-icon{
        color:inherit; }
      .bp3-menu-item.bp3-intent-warning::before, .bp3-menu-item.bp3-intent-warning::after,
      .bp3-menu-item.bp3-intent-warning .bp3-menu-item-label{
        color:#bf7326; }
      .bp3-menu-item.bp3-intent-warning:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item, .bp3-menu-item.bp3-intent-warning.bp3-active{
        background-color:#d9822b; }
      .bp3-menu-item.bp3-intent-warning:active{
        background-color:#bf7326; }
      .bp3-menu-item.bp3-intent-warning:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item, .bp3-menu-item.bp3-intent-warning:hover::before, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item::before, .bp3-menu-item.bp3-intent-warning:hover::after, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item::after,
      .bp3-menu-item.bp3-intent-warning:hover .bp3-menu-item-label,
      .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item .bp3-menu-item-label, .bp3-menu-item.bp3-intent-warning:active, .bp3-menu-item.bp3-intent-warning:active::before, .bp3-menu-item.bp3-intent-warning:active::after,
      .bp3-menu-item.bp3-intent-warning:active .bp3-menu-item-label, .bp3-menu-item.bp3-intent-warning.bp3-active, .bp3-menu-item.bp3-intent-warning.bp3-active::before, .bp3-menu-item.bp3-intent-warning.bp3-active::after,
      .bp3-menu-item.bp3-intent-warning.bp3-active .bp3-menu-item-label{
        color:#ffffff; }
    .bp3-menu-item.bp3-intent-danger{
      color:#c23030; }
      .bp3-menu-item.bp3-intent-danger .bp3-icon{
        color:inherit; }
      .bp3-menu-item.bp3-intent-danger::before, .bp3-menu-item.bp3-intent-danger::after,
      .bp3-menu-item.bp3-intent-danger .bp3-menu-item-label{
        color:#c23030; }
      .bp3-menu-item.bp3-intent-danger:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item, .bp3-menu-item.bp3-intent-danger.bp3-active{
        background-color:#db3737; }
      .bp3-menu-item.bp3-intent-danger:active{
        background-color:#c23030; }
      .bp3-menu-item.bp3-intent-danger:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item, .bp3-menu-item.bp3-intent-danger:hover::before, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item::before, .bp3-menu-item.bp3-intent-danger:hover::after, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item::after,
      .bp3-menu-item.bp3-intent-danger:hover .bp3-menu-item-label,
      .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item .bp3-menu-item-label, .bp3-menu-item.bp3-intent-danger:active, .bp3-menu-item.bp3-intent-danger:active::before, .bp3-menu-item.bp3-intent-danger:active::after,
      .bp3-menu-item.bp3-intent-danger:active .bp3-menu-item-label, .bp3-menu-item.bp3-intent-danger.bp3-active, .bp3-menu-item.bp3-intent-danger.bp3-active::before, .bp3-menu-item.bp3-intent-danger.bp3-active::after,
      .bp3-menu-item.bp3-intent-danger.bp3-active .bp3-menu-item-label{
        color:#ffffff; }
    .bp3-menu-item::before{
      font-family:"Icons16", sans-serif;
      font-size:16px;
      font-style:normal;
      font-weight:400;
      line-height:1;
      -moz-osx-font-smoothing:grayscale;
      -webkit-font-smoothing:antialiased;
      margin-right:7px; }
    .bp3-menu-item::before,
    .bp3-menu-item > .bp3-icon{
      color:#5c7080;
      margin-top:2px; }
    .bp3-menu-item .bp3-menu-item-label{
      color:#5c7080; }
    .bp3-menu-item:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-menu-item{
      color:inherit; }
    .bp3-menu-item.bp3-active, .bp3-menu-item:active{
      background-color:rgba(115, 134, 148, 0.3); }
    .bp3-menu-item.bp3-disabled{
      background-color:inherit !important;
      color:rgba(92, 112, 128, 0.6) !important;
      cursor:not-allowed !important;
      outline:none !important; }
      .bp3-menu-item.bp3-disabled::before,
      .bp3-menu-item.bp3-disabled > .bp3-icon,
      .bp3-menu-item.bp3-disabled .bp3-menu-item-label{
        color:rgba(92, 112, 128, 0.6) !important; }
    .bp3-large .bp3-menu-item{
      font-size:16px;
      line-height:22px;
      padding:9px 7px; }
      .bp3-large .bp3-menu-item .bp3-icon{
        margin-top:3px; }
      .bp3-large .bp3-menu-item::before{
        font-family:"Icons20", sans-serif;
        font-size:20px;
        font-style:normal;
        font-weight:400;
        line-height:1;
        -moz-osx-font-smoothing:grayscale;
        -webkit-font-smoothing:antialiased;
        margin-right:10px;
        margin-top:1px; }

  button.bp3-menu-item{
    background:none;
    border:none;
    text-align:left;
    width:100%; }
  .bp3-menu-header{
    border-top:1px solid rgba(16, 22, 26, 0.15);
    display:block;
    margin:5px;
    cursor:default;
    padding-left:2px; }
    .bp3-dark .bp3-menu-header{
      border-top-color:rgba(255, 255, 255, 0.15); }
    .bp3-menu-header:first-of-type{
      border-top:none; }
    .bp3-menu-header > h6{
      color:#182026;
      font-weight:600;
      overflow:hidden;
      text-overflow:ellipsis;
      white-space:nowrap;
      word-wrap:normal;
      line-height:17px;
      margin:0;
      padding:10px 7px 0 1px; }
      .bp3-dark .bp3-menu-header > h6{
        color:#f5f8fa; }
    .bp3-menu-header:first-of-type > h6{
      padding-top:0; }
    .bp3-large .bp3-menu-header > h6{
      font-size:18px;
      padding-bottom:5px;
      padding-top:15px; }
    .bp3-large .bp3-menu-header:first-of-type > h6{
      padding-top:0; }

  .bp3-dark .bp3-menu{
    background:#30404d;
    color:#f5f8fa; }

  .bp3-dark .bp3-menu-item{ }
    .bp3-dark .bp3-menu-item.bp3-intent-primary{
      color:#48aff0; }
      .bp3-dark .bp3-menu-item.bp3-intent-primary .bp3-icon{
        color:inherit; }
      .bp3-dark .bp3-menu-item.bp3-intent-primary::before, .bp3-dark .bp3-menu-item.bp3-intent-primary::after,
      .bp3-dark .bp3-menu-item.bp3-intent-primary .bp3-menu-item-label{
        color:#48aff0; }
      .bp3-dark .bp3-menu-item.bp3-intent-primary:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item, .bp3-dark .bp3-menu-item.bp3-intent-primary.bp3-active{
        background-color:#137cbd; }
      .bp3-dark .bp3-menu-item.bp3-intent-primary:active{
        background-color:#106ba3; }
      .bp3-dark .bp3-menu-item.bp3-intent-primary:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item, .bp3-dark .bp3-menu-item.bp3-intent-primary:hover::before, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item::before, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item::before, .bp3-dark .bp3-menu-item.bp3-intent-primary:hover::after, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item::after, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item::after,
      .bp3-dark .bp3-menu-item.bp3-intent-primary:hover .bp3-menu-item-label,
      .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item .bp3-menu-item-label,
      .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item .bp3-menu-item-label, .bp3-dark .bp3-menu-item.bp3-intent-primary:active, .bp3-dark .bp3-menu-item.bp3-intent-primary:active::before, .bp3-dark .bp3-menu-item.bp3-intent-primary:active::after,
      .bp3-dark .bp3-menu-item.bp3-intent-primary:active .bp3-menu-item-label, .bp3-dark .bp3-menu-item.bp3-intent-primary.bp3-active, .bp3-dark .bp3-menu-item.bp3-intent-primary.bp3-active::before, .bp3-dark .bp3-menu-item.bp3-intent-primary.bp3-active::after,
      .bp3-dark .bp3-menu-item.bp3-intent-primary.bp3-active .bp3-menu-item-label{
        color:#ffffff; }
    .bp3-dark .bp3-menu-item.bp3-intent-success{
      color:#3dcc91; }
      .bp3-dark .bp3-menu-item.bp3-intent-success .bp3-icon{
        color:inherit; }
      .bp3-dark .bp3-menu-item.bp3-intent-success::before, .bp3-dark .bp3-menu-item.bp3-intent-success::after,
      .bp3-dark .bp3-menu-item.bp3-intent-success .bp3-menu-item-label{
        color:#3dcc91; }
      .bp3-dark .bp3-menu-item.bp3-intent-success:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item, .bp3-dark .bp3-menu-item.bp3-intent-success.bp3-active{
        background-color:#0f9960; }
      .bp3-dark .bp3-menu-item.bp3-intent-success:active{
        background-color:#0d8050; }
      .bp3-dark .bp3-menu-item.bp3-intent-success:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item, .bp3-dark .bp3-menu-item.bp3-intent-success:hover::before, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item::before, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item::before, .bp3-dark .bp3-menu-item.bp3-intent-success:hover::after, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item::after, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item::after,
      .bp3-dark .bp3-menu-item.bp3-intent-success:hover .bp3-menu-item-label,
      .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item .bp3-menu-item-label,
      .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item .bp3-menu-item-label, .bp3-dark .bp3-menu-item.bp3-intent-success:active, .bp3-dark .bp3-menu-item.bp3-intent-success:active::before, .bp3-dark .bp3-menu-item.bp3-intent-success:active::after,
      .bp3-dark .bp3-menu-item.bp3-intent-success:active .bp3-menu-item-label, .bp3-dark .bp3-menu-item.bp3-intent-success.bp3-active, .bp3-dark .bp3-menu-item.bp3-intent-success.bp3-active::before, .bp3-dark .bp3-menu-item.bp3-intent-success.bp3-active::after,
      .bp3-dark .bp3-menu-item.bp3-intent-success.bp3-active .bp3-menu-item-label{
        color:#ffffff; }
    .bp3-dark .bp3-menu-item.bp3-intent-warning{
      color:#ffb366; }
      .bp3-dark .bp3-menu-item.bp3-intent-warning .bp3-icon{
        color:inherit; }
      .bp3-dark .bp3-menu-item.bp3-intent-warning::before, .bp3-dark .bp3-menu-item.bp3-intent-warning::after,
      .bp3-dark .bp3-menu-item.bp3-intent-warning .bp3-menu-item-label{
        color:#ffb366; }
      .bp3-dark .bp3-menu-item.bp3-intent-warning:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item, .bp3-dark .bp3-menu-item.bp3-intent-warning.bp3-active{
        background-color:#d9822b; }
      .bp3-dark .bp3-menu-item.bp3-intent-warning:active{
        background-color:#bf7326; }
      .bp3-dark .bp3-menu-item.bp3-intent-warning:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item, .bp3-dark .bp3-menu-item.bp3-intent-warning:hover::before, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item::before, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item::before, .bp3-dark .bp3-menu-item.bp3-intent-warning:hover::after, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item::after, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item::after,
      .bp3-dark .bp3-menu-item.bp3-intent-warning:hover .bp3-menu-item-label,
      .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item .bp3-menu-item-label,
      .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item .bp3-menu-item-label, .bp3-dark .bp3-menu-item.bp3-intent-warning:active, .bp3-dark .bp3-menu-item.bp3-intent-warning:active::before, .bp3-dark .bp3-menu-item.bp3-intent-warning:active::after,
      .bp3-dark .bp3-menu-item.bp3-intent-warning:active .bp3-menu-item-label, .bp3-dark .bp3-menu-item.bp3-intent-warning.bp3-active, .bp3-dark .bp3-menu-item.bp3-intent-warning.bp3-active::before, .bp3-dark .bp3-menu-item.bp3-intent-warning.bp3-active::after,
      .bp3-dark .bp3-menu-item.bp3-intent-warning.bp3-active .bp3-menu-item-label{
        color:#ffffff; }
    .bp3-dark .bp3-menu-item.bp3-intent-danger{
      color:#ff7373; }
      .bp3-dark .bp3-menu-item.bp3-intent-danger .bp3-icon{
        color:inherit; }
      .bp3-dark .bp3-menu-item.bp3-intent-danger::before, .bp3-dark .bp3-menu-item.bp3-intent-danger::after,
      .bp3-dark .bp3-menu-item.bp3-intent-danger .bp3-menu-item-label{
        color:#ff7373; }
      .bp3-dark .bp3-menu-item.bp3-intent-danger:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item, .bp3-dark .bp3-menu-item.bp3-intent-danger.bp3-active{
        background-color:#db3737; }
      .bp3-dark .bp3-menu-item.bp3-intent-danger:active{
        background-color:#c23030; }
      .bp3-dark .bp3-menu-item.bp3-intent-danger:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item, .bp3-dark .bp3-menu-item.bp3-intent-danger:hover::before, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item::before, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item::before, .bp3-dark .bp3-menu-item.bp3-intent-danger:hover::after, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item::after, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item::after,
      .bp3-dark .bp3-menu-item.bp3-intent-danger:hover .bp3-menu-item-label,
      .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item .bp3-menu-item-label,
      .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item .bp3-menu-item-label, .bp3-dark .bp3-menu-item.bp3-intent-danger:active, .bp3-dark .bp3-menu-item.bp3-intent-danger:active::before, .bp3-dark .bp3-menu-item.bp3-intent-danger:active::after,
      .bp3-dark .bp3-menu-item.bp3-intent-danger:active .bp3-menu-item-label, .bp3-dark .bp3-menu-item.bp3-intent-danger.bp3-active, .bp3-dark .bp3-menu-item.bp3-intent-danger.bp3-active::before, .bp3-dark .bp3-menu-item.bp3-intent-danger.bp3-active::after,
      .bp3-dark .bp3-menu-item.bp3-intent-danger.bp3-active .bp3-menu-item-label{
        color:#ffffff; }
    .bp3-dark .bp3-menu-item::before,
    .bp3-dark .bp3-menu-item > .bp3-icon{
      color:#a7b6c2; }
    .bp3-dark .bp3-menu-item .bp3-menu-item-label{
      color:#a7b6c2; }
    .bp3-dark .bp3-menu-item.bp3-active, .bp3-dark .bp3-menu-item:active{
      background-color:rgba(138, 155, 168, 0.3); }
    .bp3-dark .bp3-menu-item.bp3-disabled{
      color:rgba(167, 182, 194, 0.6) !important; }
      .bp3-dark .bp3-menu-item.bp3-disabled::before,
      .bp3-dark .bp3-menu-item.bp3-disabled > .bp3-icon,
      .bp3-dark .bp3-menu-item.bp3-disabled .bp3-menu-item-label{
        color:rgba(167, 182, 194, 0.6) !important; }

  .bp3-dark .bp3-menu-divider,
  .bp3-dark .bp3-menu-header{
    border-color:rgba(255, 255, 255, 0.15); }

  .bp3-dark .bp3-menu-header > h6{
    color:#f5f8fa; }

  .bp3-label .bp3-menu{
    margin-top:5px; }
  .bp3-navbar{
    background-color:#ffffff;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.2);
    height:50px;
    padding:0 15px;
    position:relative;
    width:100%;
    z-index:10; }
    .bp3-navbar.bp3-dark,
    .bp3-dark .bp3-navbar{
      background-color:#394b59; }
    .bp3-navbar.bp3-dark{
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-navbar{
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4); }
    .bp3-navbar.bp3-fixed-top{
      left:0;
      position:fixed;
      right:0;
      top:0; }

  .bp3-navbar-heading{
    font-size:16px;
    margin-right:15px; }

  .bp3-navbar-group{
    -webkit-box-align:center;
        -ms-flex-align:center;
            align-items:center;
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    height:50px; }
    .bp3-navbar-group.bp3-align-left{
      float:left; }
    .bp3-navbar-group.bp3-align-right{
      float:right; }

  .bp3-navbar-divider{
    border-left:1px solid rgba(16, 22, 26, 0.15);
    height:20px;
    margin:0 10px; }
    .bp3-dark .bp3-navbar-divider{
      border-left-color:rgba(255, 255, 255, 0.15); }
  .bp3-non-ideal-state{
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    -webkit-box-orient:vertical;
    -webkit-box-direction:normal;
        -ms-flex-direction:column;
            flex-direction:column;
    -webkit-box-align:center;
        -ms-flex-align:center;
            align-items:center;
    height:100%;
    -webkit-box-pack:center;
        -ms-flex-pack:center;
            justify-content:center;
    text-align:center;
    width:100%; }
    .bp3-non-ideal-state > *{
      -webkit-box-flex:0;
          -ms-flex-positive:0;
              flex-grow:0;
      -ms-flex-negative:0;
          flex-shrink:0; }
    .bp3-non-ideal-state > .bp3-fill{
      -webkit-box-flex:1;
          -ms-flex-positive:1;
              flex-grow:1;
      -ms-flex-negative:1;
          flex-shrink:1; }
    .bp3-non-ideal-state::before,
    .bp3-non-ideal-state > *{
      margin-bottom:20px; }
    .bp3-non-ideal-state:empty::before,
    .bp3-non-ideal-state > :last-child{
      margin-bottom:0; }
    .bp3-non-ideal-state > *{
      max-width:400px; }

  .bp3-non-ideal-state-visual{
    color:rgba(92, 112, 128, 0.6);
    font-size:60px; }
    .bp3-dark .bp3-non-ideal-state-visual{
      color:rgba(167, 182, 194, 0.6); }

  .bp3-overflow-list{
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    -ms-flex-wrap:nowrap;
        flex-wrap:nowrap;
    min-width:0; }

  .bp3-overflow-list-spacer{
    -ms-flex-negative:1;
        flex-shrink:1;
    width:1px; }

  body.bp3-overlay-open{
    overflow:hidden; }

  .bp3-overlay{
    bottom:0;
    left:0;
    position:static;
    right:0;
    top:0;
    z-index:20; }
    .bp3-overlay:not(.bp3-overlay-open){
      pointer-events:none; }
    .bp3-overlay.bp3-overlay-container{
      overflow:hidden;
      position:fixed; }
      .bp3-overlay.bp3-overlay-container.bp3-overlay-inline{
        position:absolute; }
    .bp3-overlay.bp3-overlay-scroll-container{
      overflow:auto;
      position:fixed; }
      .bp3-overlay.bp3-overlay-scroll-container.bp3-overlay-inline{
        position:absolute; }
    .bp3-overlay.bp3-overlay-inline{
      display:inline;
      overflow:visible; }

  .bp3-overlay-content{
    position:fixed;
    z-index:20; }
    .bp3-overlay-inline .bp3-overlay-content,
    .bp3-overlay-scroll-container .bp3-overlay-content{
      position:absolute; }

  .bp3-overlay-backdrop{
    bottom:0;
    left:0;
    position:fixed;
    right:0;
    top:0;
    opacity:1;
    background-color:rgba(16, 22, 26, 0.7);
    overflow:auto;
    -webkit-user-select:none;
      -moz-user-select:none;
        -ms-user-select:none;
            user-select:none;
    z-index:20; }
    .bp3-overlay-backdrop.bp3-overlay-enter, .bp3-overlay-backdrop.bp3-overlay-appear{
      opacity:0; }
    .bp3-overlay-backdrop.bp3-overlay-enter-active, .bp3-overlay-backdrop.bp3-overlay-appear-active{
      opacity:1;
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:200ms;
              transition-duration:200ms;
      -webkit-transition-property:opacity;
      transition-property:opacity;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-overlay-backdrop.bp3-overlay-exit{
      opacity:1; }
    .bp3-overlay-backdrop.bp3-overlay-exit-active{
      opacity:0;
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:200ms;
              transition-duration:200ms;
      -webkit-transition-property:opacity;
      transition-property:opacity;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-overlay-backdrop:focus{
      outline:none; }
    .bp3-overlay-inline .bp3-overlay-backdrop{
      position:absolute; }
  .bp3-panel-stack{
    overflow:hidden;
    position:relative; }

  .bp3-panel-stack-header{
    -webkit-box-align:center;
        -ms-flex-align:center;
            align-items:center;
    -webkit-box-shadow:0 1px rgba(16, 22, 26, 0.15);
            box-shadow:0 1px rgba(16, 22, 26, 0.15);
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    -ms-flex-negative:0;
        flex-shrink:0;
    height:30px;
    z-index:1; }
    .bp3-dark .bp3-panel-stack-header{
      -webkit-box-shadow:0 1px rgba(255, 255, 255, 0.15);
              box-shadow:0 1px rgba(255, 255, 255, 0.15); }
    .bp3-panel-stack-header > span{
      -webkit-box-align:stretch;
          -ms-flex-align:stretch;
              align-items:stretch;
      display:-webkit-box;
      display:-ms-flexbox;
      display:flex;
      -webkit-box-flex:1;
          -ms-flex:1;
              flex:1; }
    .bp3-panel-stack-header .bp3-heading{
      margin:0 5px; }

  .bp3-button.bp3-panel-stack-header-back{
    margin-left:5px;
    padding-left:0;
    white-space:nowrap; }
    .bp3-button.bp3-panel-stack-header-back .bp3-icon{
      margin:0 2px; }

  .bp3-panel-stack-view{
    bottom:0;
    left:0;
    position:absolute;
    right:0;
    top:0;
    background-color:#ffffff;
    border-right:1px solid rgba(16, 22, 26, 0.15);
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    -webkit-box-orient:vertical;
    -webkit-box-direction:normal;
        -ms-flex-direction:column;
            flex-direction:column;
    margin-right:-1px;
    overflow-y:auto;
    z-index:1; }
    .bp3-dark .bp3-panel-stack-view{
      background-color:#30404d; }
    .bp3-panel-stack-view:nth-last-child(n + 4){
      display:none; }

  .bp3-panel-stack-push .bp3-panel-stack-enter, .bp3-panel-stack-push .bp3-panel-stack-appear{
    -webkit-transform:translateX(100%);
            transform:translateX(100%);
    opacity:0; }

  .bp3-panel-stack-push .bp3-panel-stack-enter-active, .bp3-panel-stack-push .bp3-panel-stack-appear-active{
    -webkit-transform:translate(0%);
            transform:translate(0%);
    opacity:1;
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:400ms;
            transition-duration:400ms;
    -webkit-transition-property:opacity, -webkit-transform;
    transition-property:opacity, -webkit-transform;
    transition-property:transform, opacity;
    transition-property:transform, opacity, -webkit-transform;
    -webkit-transition-timing-function:ease;
            transition-timing-function:ease; }

  .bp3-panel-stack-push .bp3-panel-stack-exit{
    -webkit-transform:translate(0%);
            transform:translate(0%);
    opacity:1; }

  .bp3-panel-stack-push .bp3-panel-stack-exit-active{
    -webkit-transform:translateX(-50%);
            transform:translateX(-50%);
    opacity:0;
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:400ms;
            transition-duration:400ms;
    -webkit-transition-property:opacity, -webkit-transform;
    transition-property:opacity, -webkit-transform;
    transition-property:transform, opacity;
    transition-property:transform, opacity, -webkit-transform;
    -webkit-transition-timing-function:ease;
            transition-timing-function:ease; }

  .bp3-panel-stack-pop .bp3-panel-stack-enter, .bp3-panel-stack-pop .bp3-panel-stack-appear{
    -webkit-transform:translateX(-50%);
            transform:translateX(-50%);
    opacity:0; }

  .bp3-panel-stack-pop .bp3-panel-stack-enter-active, .bp3-panel-stack-pop .bp3-panel-stack-appear-active{
    -webkit-transform:translate(0%);
            transform:translate(0%);
    opacity:1;
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:400ms;
            transition-duration:400ms;
    -webkit-transition-property:opacity, -webkit-transform;
    transition-property:opacity, -webkit-transform;
    transition-property:transform, opacity;
    transition-property:transform, opacity, -webkit-transform;
    -webkit-transition-timing-function:ease;
            transition-timing-function:ease; }

  .bp3-panel-stack-pop .bp3-panel-stack-exit{
    -webkit-transform:translate(0%);
            transform:translate(0%);
    opacity:1; }

  .bp3-panel-stack-pop .bp3-panel-stack-exit-active{
    -webkit-transform:translateX(100%);
            transform:translateX(100%);
    opacity:0;
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:400ms;
            transition-duration:400ms;
    -webkit-transition-property:opacity, -webkit-transform;
    transition-property:opacity, -webkit-transform;
    transition-property:transform, opacity;
    transition-property:transform, opacity, -webkit-transform;
    -webkit-transition-timing-function:ease;
            transition-timing-function:ease; }
  .bp3-popover{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
    -webkit-transform:scale(1);
            transform:scale(1);
    border-radius:3px;
    display:inline-block;
    z-index:20; }
    .bp3-popover .bp3-popover-arrow{
      height:30px;
      position:absolute;
      width:30px; }
      .bp3-popover .bp3-popover-arrow::before{
        height:20px;
        margin:5px;
        width:20px; }
    .bp3-tether-element-attached-bottom.bp3-tether-target-attached-top > .bp3-popover{
      margin-bottom:17px;
      margin-top:-17px; }
      .bp3-tether-element-attached-bottom.bp3-tether-target-attached-top > .bp3-popover > .bp3-popover-arrow{
        bottom:-11px; }
        .bp3-tether-element-attached-bottom.bp3-tether-target-attached-top > .bp3-popover > .bp3-popover-arrow svg{
          -webkit-transform:rotate(-90deg);
                  transform:rotate(-90deg); }
    .bp3-tether-element-attached-left.bp3-tether-target-attached-right > .bp3-popover{
      margin-left:17px; }
      .bp3-tether-element-attached-left.bp3-tether-target-attached-right > .bp3-popover > .bp3-popover-arrow{
        left:-11px; }
        .bp3-tether-element-attached-left.bp3-tether-target-attached-right > .bp3-popover > .bp3-popover-arrow svg{
          -webkit-transform:rotate(0);
                  transform:rotate(0); }
    .bp3-tether-element-attached-top.bp3-tether-target-attached-bottom > .bp3-popover{
      margin-top:17px; }
      .bp3-tether-element-attached-top.bp3-tether-target-attached-bottom > .bp3-popover > .bp3-popover-arrow{
        top:-11px; }
        .bp3-tether-element-attached-top.bp3-tether-target-attached-bottom > .bp3-popover > .bp3-popover-arrow svg{
          -webkit-transform:rotate(90deg);
                  transform:rotate(90deg); }
    .bp3-tether-element-attached-right.bp3-tether-target-attached-left > .bp3-popover{
      margin-left:-17px;
      margin-right:17px; }
      .bp3-tether-element-attached-right.bp3-tether-target-attached-left > .bp3-popover > .bp3-popover-arrow{
        right:-11px; }
        .bp3-tether-element-attached-right.bp3-tether-target-attached-left > .bp3-popover > .bp3-popover-arrow svg{
          -webkit-transform:rotate(180deg);
                  transform:rotate(180deg); }
    .bp3-tether-element-attached-middle > .bp3-popover > .bp3-popover-arrow{
      top:50%;
      -webkit-transform:translateY(-50%);
              transform:translateY(-50%); }
    .bp3-tether-element-attached-center > .bp3-popover > .bp3-popover-arrow{
      right:50%;
      -webkit-transform:translateX(50%);
              transform:translateX(50%); }
    .bp3-tether-element-attached-top.bp3-tether-target-attached-top > .bp3-popover > .bp3-popover-arrow{
      top:-0.3934px; }
    .bp3-tether-element-attached-right.bp3-tether-target-attached-right > .bp3-popover > .bp3-popover-arrow{
      right:-0.3934px; }
    .bp3-tether-element-attached-left.bp3-tether-target-attached-left > .bp3-popover > .bp3-popover-arrow{
      left:-0.3934px; }
    .bp3-tether-element-attached-bottom.bp3-tether-target-attached-bottom > .bp3-popover > .bp3-popover-arrow{
      bottom:-0.3934px; }
    .bp3-tether-element-attached-top.bp3-tether-element-attached-left > .bp3-popover{
      -webkit-transform-origin:top left;
              transform-origin:top left; }
    .bp3-tether-element-attached-top.bp3-tether-element-attached-center > .bp3-popover{
      -webkit-transform-origin:top center;
              transform-origin:top center; }
    .bp3-tether-element-attached-top.bp3-tether-element-attached-right > .bp3-popover{
      -webkit-transform-origin:top right;
              transform-origin:top right; }
    .bp3-tether-element-attached-middle.bp3-tether-element-attached-left > .bp3-popover{
      -webkit-transform-origin:center left;
              transform-origin:center left; }
    .bp3-tether-element-attached-middle.bp3-tether-element-attached-center > .bp3-popover{
      -webkit-transform-origin:center center;
              transform-origin:center center; }
    .bp3-tether-element-attached-middle.bp3-tether-element-attached-right > .bp3-popover{
      -webkit-transform-origin:center right;
              transform-origin:center right; }
    .bp3-tether-element-attached-bottom.bp3-tether-element-attached-left > .bp3-popover{
      -webkit-transform-origin:bottom left;
              transform-origin:bottom left; }
    .bp3-tether-element-attached-bottom.bp3-tether-element-attached-center > .bp3-popover{
      -webkit-transform-origin:bottom center;
              transform-origin:bottom center; }
    .bp3-tether-element-attached-bottom.bp3-tether-element-attached-right > .bp3-popover{
      -webkit-transform-origin:bottom right;
              transform-origin:bottom right; }
    .bp3-popover .bp3-popover-content{
      background:#ffffff;
      color:inherit; }
    .bp3-popover .bp3-popover-arrow::before{
      -webkit-box-shadow:1px 1px 6px rgba(16, 22, 26, 0.2);
              box-shadow:1px 1px 6px rgba(16, 22, 26, 0.2); }
    .bp3-popover .bp3-popover-arrow-border{
      fill:#10161a;
      fill-opacity:0.1; }
    .bp3-popover .bp3-popover-arrow-fill{
      fill:#ffffff; }
    .bp3-popover-enter > .bp3-popover, .bp3-popover-appear > .bp3-popover{
      -webkit-transform:scale(0.3);
              transform:scale(0.3); }
    .bp3-popover-enter-active > .bp3-popover, .bp3-popover-appear-active > .bp3-popover{
      -webkit-transform:scale(1);
              transform:scale(1);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:300ms;
              transition-duration:300ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11);
              transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11); }
    .bp3-popover-exit > .bp3-popover{
      -webkit-transform:scale(1);
              transform:scale(1); }
    .bp3-popover-exit-active > .bp3-popover{
      -webkit-transform:scale(0.3);
              transform:scale(0.3);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:300ms;
              transition-duration:300ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11);
              transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11); }
    .bp3-popover .bp3-popover-content{
      border-radius:3px;
      position:relative; }
    .bp3-popover.bp3-popover-content-sizing .bp3-popover-content{
      max-width:350px;
      padding:20px; }
    .bp3-popover-target + .bp3-overlay .bp3-popover.bp3-popover-content-sizing{
      width:350px; }
    .bp3-popover.bp3-minimal{
      margin:0 !important; }
      .bp3-popover.bp3-minimal .bp3-popover-arrow{
        display:none; }
      .bp3-popover.bp3-minimal.bp3-popover{
        -webkit-transform:scale(1);
                transform:scale(1); }
        .bp3-popover-enter > .bp3-popover.bp3-minimal.bp3-popover, .bp3-popover-appear > .bp3-popover.bp3-minimal.bp3-popover{
          -webkit-transform:scale(1);
                  transform:scale(1); }
        .bp3-popover-enter-active > .bp3-popover.bp3-minimal.bp3-popover, .bp3-popover-appear-active > .bp3-popover.bp3-minimal.bp3-popover{
          -webkit-transform:scale(1);
                  transform:scale(1);
          -webkit-transition-delay:0;
                  transition-delay:0;
          -webkit-transition-duration:100ms;
                  transition-duration:100ms;
          -webkit-transition-property:-webkit-transform;
          transition-property:-webkit-transform;
          transition-property:transform;
          transition-property:transform, -webkit-transform;
          -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
                  transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
        .bp3-popover-exit > .bp3-popover.bp3-minimal.bp3-popover{
          -webkit-transform:scale(1);
                  transform:scale(1); }
        .bp3-popover-exit-active > .bp3-popover.bp3-minimal.bp3-popover{
          -webkit-transform:scale(1);
                  transform:scale(1);
          -webkit-transition-delay:0;
                  transition-delay:0;
          -webkit-transition-duration:100ms;
                  transition-duration:100ms;
          -webkit-transition-property:-webkit-transform;
          transition-property:-webkit-transform;
          transition-property:transform;
          transition-property:transform, -webkit-transform;
          -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
                  transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-popover.bp3-dark,
    .bp3-dark .bp3-popover{
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4); }
      .bp3-popover.bp3-dark .bp3-popover-content,
      .bp3-dark .bp3-popover .bp3-popover-content{
        background:#30404d;
        color:inherit; }
      .bp3-popover.bp3-dark .bp3-popover-arrow::before,
      .bp3-dark .bp3-popover .bp3-popover-arrow::before{
        -webkit-box-shadow:1px 1px 6px rgba(16, 22, 26, 0.4);
                box-shadow:1px 1px 6px rgba(16, 22, 26, 0.4); }
      .bp3-popover.bp3-dark .bp3-popover-arrow-border,
      .bp3-dark .bp3-popover .bp3-popover-arrow-border{
        fill:#10161a;
        fill-opacity:0.2; }
      .bp3-popover.bp3-dark .bp3-popover-arrow-fill,
      .bp3-dark .bp3-popover .bp3-popover-arrow-fill{
        fill:#30404d; }

  .bp3-popover-arrow::before{
    border-radius:2px;
    content:"";
    display:block;
    position:absolute;
    -webkit-transform:rotate(45deg);
            transform:rotate(45deg); }

  .bp3-tether-pinned .bp3-popover-arrow{
    display:none; }

  .bp3-popover-backdrop{
    background:rgba(255, 255, 255, 0); }

  .bp3-transition-container{
    opacity:1;
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    z-index:20; }
    .bp3-transition-container.bp3-popover-enter, .bp3-transition-container.bp3-popover-appear{
      opacity:0; }
    .bp3-transition-container.bp3-popover-enter-active, .bp3-transition-container.bp3-popover-appear-active{
      opacity:1;
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:100ms;
              transition-duration:100ms;
      -webkit-transition-property:opacity;
      transition-property:opacity;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-transition-container.bp3-popover-exit{
      opacity:1; }
    .bp3-transition-container.bp3-popover-exit-active{
      opacity:0;
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:100ms;
              transition-duration:100ms;
      -webkit-transition-property:opacity;
      transition-property:opacity;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-transition-container:focus{
      outline:none; }
    .bp3-transition-container.bp3-popover-leave .bp3-popover-content{
      pointer-events:none; }
    .bp3-transition-container[data-x-out-of-boundaries]{
      display:none; }

  span.bp3-popover-target{
    display:inline-block; }

  .bp3-popover-wrapper.bp3-fill{
    width:100%; }

  .bp3-portal{
    left:0;
    position:absolute;
    right:0;
    top:0; }
  @-webkit-keyframes linear-progress-bar-stripes{
    from{
      background-position:0 0; }
    to{
      background-position:30px 0; } }
  @keyframes linear-progress-bar-stripes{
    from{
      background-position:0 0; }
    to{
      background-position:30px 0; } }

  .bp3-progress-bar{
    background:rgba(92, 112, 128, 0.2);
    border-radius:40px;
    display:block;
    height:8px;
    overflow:hidden;
    position:relative;
    width:100%; }
    .bp3-progress-bar .bp3-progress-meter{
      background:linear-gradient(-45deg, rgba(255, 255, 255, 0.2) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.2) 50%, rgba(255, 255, 255, 0.2) 75%, transparent 75%);
      background-color:rgba(92, 112, 128, 0.8);
      background-size:30px 30px;
      border-radius:40px;
      height:100%;
      position:absolute;
      -webkit-transition:width 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
      transition:width 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
      width:100%; }
    .bp3-progress-bar:not(.bp3-no-animation):not(.bp3-no-stripes) .bp3-progress-meter{
      animation:linear-progress-bar-stripes 300ms linear infinite reverse; }
    .bp3-progress-bar.bp3-no-stripes .bp3-progress-meter{
      background-image:none; }

  .bp3-dark .bp3-progress-bar{
    background:rgba(16, 22, 26, 0.5); }
    .bp3-dark .bp3-progress-bar .bp3-progress-meter{
      background-color:#8a9ba8; }

  .bp3-progress-bar.bp3-intent-primary .bp3-progress-meter{
    background-color:#137cbd; }

  .bp3-progress-bar.bp3-intent-success .bp3-progress-meter{
    background-color:#0f9960; }

  .bp3-progress-bar.bp3-intent-warning .bp3-progress-meter{
    background-color:#d9822b; }

  .bp3-progress-bar.bp3-intent-danger .bp3-progress-meter{
    background-color:#db3737; }
  @-webkit-keyframes skeleton-glow{
    from{
      background:rgba(206, 217, 224, 0.2);
      border-color:rgba(206, 217, 224, 0.2); }
    to{
      background:rgba(92, 112, 128, 0.2);
      border-color:rgba(92, 112, 128, 0.2); } }
  @keyframes skeleton-glow{
    from{
      background:rgba(206, 217, 224, 0.2);
      border-color:rgba(206, 217, 224, 0.2); }
    to{
      background:rgba(92, 112, 128, 0.2);
      border-color:rgba(92, 112, 128, 0.2); } }
  .bp3-skeleton{
    -webkit-animation:1000ms linear infinite alternate skeleton-glow;
            animation:1000ms linear infinite alternate skeleton-glow;
    background:rgba(206, 217, 224, 0.2);
    background-clip:padding-box !important;
    border-color:rgba(206, 217, 224, 0.2) !important;
    border-radius:2px;
    -webkit-box-shadow:none !important;
            box-shadow:none !important;
    color:transparent !important;
    cursor:default;
    pointer-events:none;
    -webkit-user-select:none;
      -moz-user-select:none;
        -ms-user-select:none;
            user-select:none; }
    .bp3-skeleton::before, .bp3-skeleton::after,
    .bp3-skeleton *{
      visibility:hidden !important; }
  .bp3-slider{
    height:40px;
    min-width:150px;
    width:100%;
    cursor:default;
    outline:none;
    position:relative;
    -webkit-user-select:none;
      -moz-user-select:none;
        -ms-user-select:none;
            user-select:none; }
    .bp3-slider:hover{
      cursor:pointer; }
    .bp3-slider:active{
      cursor:-webkit-grabbing;
      cursor:grabbing; }
    .bp3-slider.bp3-disabled{
      cursor:not-allowed;
      opacity:0.5; }
    .bp3-slider.bp3-slider-unlabeled{
      height:16px; }

  .bp3-slider-track,
  .bp3-slider-progress{
    height:6px;
    left:0;
    right:0;
    top:5px;
    position:absolute; }

  .bp3-slider-track{
    border-radius:3px;
    overflow:hidden; }

  .bp3-slider-progress{
    background:rgba(92, 112, 128, 0.2); }
    .bp3-dark .bp3-slider-progress{
      background:rgba(16, 22, 26, 0.5); }
    .bp3-slider-progress.bp3-intent-primary{
      background-color:#137cbd; }
    .bp3-slider-progress.bp3-intent-success{
      background-color:#0f9960; }
    .bp3-slider-progress.bp3-intent-warning{
      background-color:#d9822b; }
    .bp3-slider-progress.bp3-intent-danger{
      background-color:#db3737; }

  .bp3-slider-handle{
    background-color:#f5f8fa;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.8)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.8), rgba(255, 255, 255, 0));
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
    color:#182026;
    border-radius:3px;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 1px 1px rgba(16, 22, 26, 0.2);
    cursor:pointer;
    height:16px;
    left:0;
    position:absolute;
    top:0;
    width:16px; }
    .bp3-slider-handle:hover{
      background-clip:padding-box;
      background-color:#ebf1f5;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1); }
    .bp3-slider-handle:active, .bp3-slider-handle.bp3-active{
      background-color:#d8e1e8;
      background-image:none;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
    .bp3-slider-handle:disabled, .bp3-slider-handle.bp3-disabled{
      background-color:rgba(206, 217, 224, 0.5);
      background-image:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(92, 112, 128, 0.6);
      cursor:not-allowed;
      outline:none; }
      .bp3-slider-handle:disabled.bp3-active, .bp3-slider-handle:disabled.bp3-active:hover, .bp3-slider-handle.bp3-disabled.bp3-active, .bp3-slider-handle.bp3-disabled.bp3-active:hover{
        background:rgba(206, 217, 224, 0.7); }
    .bp3-slider-handle:focus{
      z-index:1; }
    .bp3-slider-handle:hover{
      background-clip:padding-box;
      background-color:#ebf1f5;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 1px 1px rgba(16, 22, 26, 0.2);
      cursor:-webkit-grab;
      cursor:grab;
      z-index:2; }
    .bp3-slider-handle.bp3-active{
      background-color:#d8e1e8;
      background-image:none;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 1px rgba(16, 22, 26, 0.1);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 1px rgba(16, 22, 26, 0.1);
      cursor:-webkit-grabbing;
      cursor:grabbing; }
    .bp3-disabled .bp3-slider-handle{
      background:#bfccd6;
      -webkit-box-shadow:none;
              box-shadow:none;
      pointer-events:none; }
    .bp3-dark .bp3-slider-handle{
      background-color:#394b59;
      background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.05)), to(rgba(255, 255, 255, 0)));
      background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.05), rgba(255, 255, 255, 0));
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
      color:#f5f8fa; }
      .bp3-dark .bp3-slider-handle:hover, .bp3-dark .bp3-slider-handle:active, .bp3-dark .bp3-slider-handle.bp3-active{
        color:#f5f8fa; }
      .bp3-dark .bp3-slider-handle:hover{
        background-color:#30404d;
        -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
                box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-slider-handle:active, .bp3-dark .bp3-slider-handle.bp3-active{
        background-color:#202b33;
        background-image:none;
        -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2);
                box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
      .bp3-dark .bp3-slider-handle:disabled, .bp3-dark .bp3-slider-handle.bp3-disabled{
        background-color:rgba(57, 75, 89, 0.5);
        background-image:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:rgba(167, 182, 194, 0.6); }
        .bp3-dark .bp3-slider-handle:disabled.bp3-active, .bp3-dark .bp3-slider-handle.bp3-disabled.bp3-active{
          background:rgba(57, 75, 89, 0.7); }
      .bp3-dark .bp3-slider-handle .bp3-button-spinner .bp3-spinner-head{
        background:rgba(16, 22, 26, 0.5);
        stroke:#8a9ba8; }
      .bp3-dark .bp3-slider-handle, .bp3-dark .bp3-slider-handle:hover{
        background-color:#394b59; }
      .bp3-dark .bp3-slider-handle.bp3-active{
        background-color:#293742; }
    .bp3-dark .bp3-disabled .bp3-slider-handle{
      background:#5c7080;
      border-color:#5c7080;
      -webkit-box-shadow:none;
              box-shadow:none; }
    .bp3-slider-handle .bp3-slider-label{
      background:#394b59;
      border-radius:3px;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
      color:#f5f8fa;
      margin-left:8px; }
      .bp3-dark .bp3-slider-handle .bp3-slider-label{
        background:#e1e8ed;
        -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
                box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
        color:#394b59; }
      .bp3-disabled .bp3-slider-handle .bp3-slider-label{
        -webkit-box-shadow:none;
                box-shadow:none; }
    .bp3-slider-handle.bp3-start, .bp3-slider-handle.bp3-end{
      width:8px; }
    .bp3-slider-handle.bp3-start{
      border-bottom-right-radius:0;
      border-top-right-radius:0; }
    .bp3-slider-handle.bp3-end{
      border-bottom-left-radius:0;
      border-top-left-radius:0;
      margin-left:8px; }
      .bp3-slider-handle.bp3-end .bp3-slider-label{
        margin-left:0; }

  .bp3-slider-label{
    -webkit-transform:translate(-50%, 20px);
            transform:translate(-50%, 20px);
    display:inline-block;
    font-size:12px;
    line-height:1;
    padding:2px 5px;
    position:absolute;
    vertical-align:top; }

  .bp3-slider.bp3-vertical{
    height:150px;
    min-width:40px;
    width:40px; }
    .bp3-slider.bp3-vertical .bp3-slider-track,
    .bp3-slider.bp3-vertical .bp3-slider-progress{
      bottom:0;
      height:auto;
      left:5px;
      top:0;
      width:6px; }
    .bp3-slider.bp3-vertical .bp3-slider-progress{
      top:auto; }
    .bp3-slider.bp3-vertical .bp3-slider-label{
      -webkit-transform:translate(20px, 50%);
              transform:translate(20px, 50%); }
    .bp3-slider.bp3-vertical .bp3-slider-handle{
      top:auto; }
      .bp3-slider.bp3-vertical .bp3-slider-handle .bp3-slider-label{
        margin-left:0;
        margin-top:-8px; }
      .bp3-slider.bp3-vertical .bp3-slider-handle.bp3-end, .bp3-slider.bp3-vertical .bp3-slider-handle.bp3-start{
        height:8px;
        margin-left:0;
        width:16px; }
      .bp3-slider.bp3-vertical .bp3-slider-handle.bp3-start{
        border-bottom-right-radius:3px;
        border-top-left-radius:0; }
        .bp3-slider.bp3-vertical .bp3-slider-handle.bp3-start .bp3-slider-label{
          -webkit-transform:translate(20px);
                  transform:translate(20px); }
      .bp3-slider.bp3-vertical .bp3-slider-handle.bp3-end{
        border-bottom-left-radius:0;
        border-bottom-right-radius:0;
        border-top-left-radius:3px;
        margin-bottom:8px; }

  @-webkit-keyframes pt-spinner-animation{
    from{
      -webkit-transform:rotate(0deg);
              transform:rotate(0deg); }
    to{
      -webkit-transform:rotate(360deg);
              transform:rotate(360deg); } }

  @keyframes pt-spinner-animation{
    from{
      -webkit-transform:rotate(0deg);
              transform:rotate(0deg); }
    to{
      -webkit-transform:rotate(360deg);
              transform:rotate(360deg); } }

  .bp3-spinner{
    -webkit-box-align:center;
        -ms-flex-align:center;
            align-items:center;
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    -webkit-box-pack:center;
        -ms-flex-pack:center;
            justify-content:center;
    overflow:visible;
    vertical-align:middle; }
    .bp3-spinner svg{
      display:block; }
    .bp3-spinner path{
      fill-opacity:0; }
    .bp3-spinner .bp3-spinner-head{
      stroke:rgba(92, 112, 128, 0.8);
      stroke-linecap:round;
      -webkit-transform-origin:center;
              transform-origin:center;
      -webkit-transition:stroke-dashoffset 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
      transition:stroke-dashoffset 200ms cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-spinner .bp3-spinner-track{
      stroke:rgba(92, 112, 128, 0.2); }

  .bp3-spinner-animation{
    -webkit-animation:pt-spinner-animation 500ms linear infinite;
            animation:pt-spinner-animation 500ms linear infinite; }
    .bp3-no-spin > .bp3-spinner-animation{
      -webkit-animation:none;
              animation:none; }

  .bp3-dark .bp3-spinner .bp3-spinner-head{
    stroke:#8a9ba8; }

  .bp3-dark .bp3-spinner .bp3-spinner-track{
    stroke:rgba(16, 22, 26, 0.5); }

  .bp3-spinner.bp3-intent-primary .bp3-spinner-head{
    stroke:#137cbd; }

  .bp3-spinner.bp3-intent-success .bp3-spinner-head{
    stroke:#0f9960; }

  .bp3-spinner.bp3-intent-warning .bp3-spinner-head{
    stroke:#d9822b; }

  .bp3-spinner.bp3-intent-danger .bp3-spinner-head{
    stroke:#db3737; }
  .bp3-tabs.bp3-vertical{
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex; }
    .bp3-tabs.bp3-vertical > .bp3-tab-list{
      -webkit-box-align:start;
          -ms-flex-align:start;
              align-items:flex-start;
      -webkit-box-orient:vertical;
      -webkit-box-direction:normal;
          -ms-flex-direction:column;
              flex-direction:column; }
      .bp3-tabs.bp3-vertical > .bp3-tab-list .bp3-tab{
        border-radius:3px;
        padding:0 10px;
        width:100%; }
        .bp3-tabs.bp3-vertical > .bp3-tab-list .bp3-tab[aria-selected="true"]{
          background-color:rgba(19, 124, 189, 0.2);
          -webkit-box-shadow:none;
                  box-shadow:none; }
      .bp3-tabs.bp3-vertical > .bp3-tab-list .bp3-tab-indicator-wrapper .bp3-tab-indicator{
        background-color:rgba(19, 124, 189, 0.2);
        border-radius:3px;
        bottom:0;
        height:auto;
        left:0;
        right:0;
        top:0; }
    .bp3-tabs.bp3-vertical > .bp3-tab-panel{
      margin-top:0;
      padding-left:20px; }

  .bp3-tab-list{
    -webkit-box-align:end;
        -ms-flex-align:end;
            align-items:flex-end;
    border:none;
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    -webkit-box-flex:0;
        -ms-flex:0 0 auto;
            flex:0 0 auto;
    list-style:none;
    margin:0;
    padding:0;
    position:relative; }
    .bp3-tab-list > *:not(:last-child){
      margin-right:20px; }

  .bp3-tab{
    overflow:hidden;
    text-overflow:ellipsis;
    white-space:nowrap;
    word-wrap:normal;
    color:#182026;
    cursor:pointer;
    -webkit-box-flex:0;
        -ms-flex:0 0 auto;
            flex:0 0 auto;
    font-size:14px;
    line-height:30px;
    max-width:100%;
    position:relative;
    vertical-align:top; }
    .bp3-tab a{
      color:inherit;
      display:block;
      text-decoration:none; }
    .bp3-tab-indicator-wrapper ~ .bp3-tab{
      background-color:transparent !important;
      -webkit-box-shadow:none !important;
              box-shadow:none !important; }
    .bp3-tab[aria-disabled="true"]{
      color:rgba(92, 112, 128, 0.6);
      cursor:not-allowed; }
    .bp3-tab[aria-selected="true"]{
      border-radius:0;
      -webkit-box-shadow:inset 0 -3px 0 #106ba3;
              box-shadow:inset 0 -3px 0 #106ba3; }
    .bp3-tab[aria-selected="true"], .bp3-tab:not([aria-disabled="true"]):hover{
      color:#106ba3; }
    .bp3-tab:focus{
      -moz-outline-radius:0; }
    .bp3-large > .bp3-tab{
      font-size:16px;
      line-height:40px; }

  .bp3-tab-panel{
    margin-top:20px; }
    .bp3-tab-panel[aria-hidden="true"]{
      display:none; }

  .bp3-tab-indicator-wrapper{
    left:0;
    pointer-events:none;
    position:absolute;
    top:0;
    -webkit-transform:translateX(0), translateY(0);
            transform:translateX(0), translateY(0);
    -webkit-transition:height, width, -webkit-transform;
    transition:height, width, -webkit-transform;
    transition:height, transform, width;
    transition:height, transform, width, -webkit-transform;
    -webkit-transition-duration:200ms;
            transition-duration:200ms;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-tab-indicator-wrapper .bp3-tab-indicator{
      background-color:#106ba3;
      bottom:0;
      height:3px;
      left:0;
      position:absolute;
      right:0; }
    .bp3-tab-indicator-wrapper.bp3-no-animation{
      -webkit-transition:none;
      transition:none; }

  .bp3-dark .bp3-tab{
    color:#f5f8fa; }
    .bp3-dark .bp3-tab[aria-disabled="true"]{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-tab[aria-selected="true"]{
      -webkit-box-shadow:inset 0 -3px 0 #48aff0;
              box-shadow:inset 0 -3px 0 #48aff0; }
    .bp3-dark .bp3-tab[aria-selected="true"], .bp3-dark .bp3-tab:not([aria-disabled="true"]):hover{
      color:#48aff0; }

  .bp3-dark .bp3-tab-indicator{
    background-color:#48aff0; }

  .bp3-flex-expander{
    -webkit-box-flex:1;
        -ms-flex:1 1;
            flex:1 1; }
  .bp3-tag{
    display:-webkit-inline-box;
    display:-ms-inline-flexbox;
    display:inline-flex;
    -webkit-box-orient:horizontal;
    -webkit-box-direction:normal;
        -ms-flex-direction:row;
            flex-direction:row;
    -webkit-box-align:center;
        -ms-flex-align:center;
            align-items:center;
    background-color:#5c7080;
    border:none;
    border-radius:3px;
    -webkit-box-shadow:none;
            box-shadow:none;
    color:#f5f8fa;
    font-size:12px;
    line-height:16px;
    max-width:100%;
    min-height:20px;
    min-width:20px;
    padding:2px 6px;
    position:relative; }
    .bp3-tag.bp3-interactive{
      cursor:pointer; }
      .bp3-tag.bp3-interactive:hover{
        background-color:rgba(92, 112, 128, 0.85); }
      .bp3-tag.bp3-interactive.bp3-active, .bp3-tag.bp3-interactive:active{
        background-color:rgba(92, 112, 128, 0.7); }
    .bp3-tag > *{
      -webkit-box-flex:0;
          -ms-flex-positive:0;
              flex-grow:0;
      -ms-flex-negative:0;
          flex-shrink:0; }
    .bp3-tag > .bp3-fill{
      -webkit-box-flex:1;
          -ms-flex-positive:1;
              flex-grow:1;
      -ms-flex-negative:1;
          flex-shrink:1; }
    .bp3-tag::before,
    .bp3-tag > *{
      margin-right:4px; }
    .bp3-tag:empty::before,
    .bp3-tag > :last-child{
      margin-right:0; }
    .bp3-tag:focus{
      outline:rgba(19, 124, 189, 0.6) auto 2px;
      outline-offset:0;
      -moz-outline-radius:6px; }
    .bp3-tag.bp3-round{
      border-radius:30px;
      padding-left:8px;
      padding-right:8px; }
    .bp3-dark .bp3-tag{
      background-color:#bfccd6;
      color:#182026; }
      .bp3-dark .bp3-tag.bp3-interactive{
        cursor:pointer; }
        .bp3-dark .bp3-tag.bp3-interactive:hover{
          background-color:rgba(191, 204, 214, 0.85); }
        .bp3-dark .bp3-tag.bp3-interactive.bp3-active, .bp3-dark .bp3-tag.bp3-interactive:active{
          background-color:rgba(191, 204, 214, 0.7); }
      .bp3-dark .bp3-tag > .bp3-icon, .bp3-dark .bp3-tag .bp3-icon-standard, .bp3-dark .bp3-tag .bp3-icon-large{
        fill:currentColor; }
    .bp3-tag > .bp3-icon, .bp3-tag .bp3-icon-standard, .bp3-tag .bp3-icon-large{
      fill:#ffffff; }
    .bp3-tag.bp3-large,
    .bp3-large .bp3-tag{
      font-size:14px;
      line-height:20px;
      min-height:30px;
      min-width:30px;
      padding:5px 10px; }
      .bp3-tag.bp3-large::before,
      .bp3-tag.bp3-large > *,
      .bp3-large .bp3-tag::before,
      .bp3-large .bp3-tag > *{
        margin-right:7px; }
      .bp3-tag.bp3-large:empty::before,
      .bp3-tag.bp3-large > :last-child,
      .bp3-large .bp3-tag:empty::before,
      .bp3-large .bp3-tag > :last-child{
        margin-right:0; }
      .bp3-tag.bp3-large.bp3-round,
      .bp3-large .bp3-tag.bp3-round{
        padding-left:12px;
        padding-right:12px; }
    .bp3-tag.bp3-intent-primary{
      background:#137cbd;
      color:#ffffff; }
      .bp3-tag.bp3-intent-primary.bp3-interactive{
        cursor:pointer; }
        .bp3-tag.bp3-intent-primary.bp3-interactive:hover{
          background-color:rgba(19, 124, 189, 0.85); }
        .bp3-tag.bp3-intent-primary.bp3-interactive.bp3-active, .bp3-tag.bp3-intent-primary.bp3-interactive:active{
          background-color:rgba(19, 124, 189, 0.7); }
    .bp3-tag.bp3-intent-success{
      background:#0f9960;
      color:#ffffff; }
      .bp3-tag.bp3-intent-success.bp3-interactive{
        cursor:pointer; }
        .bp3-tag.bp3-intent-success.bp3-interactive:hover{
          background-color:rgba(15, 153, 96, 0.85); }
        .bp3-tag.bp3-intent-success.bp3-interactive.bp3-active, .bp3-tag.bp3-intent-success.bp3-interactive:active{
          background-color:rgba(15, 153, 96, 0.7); }
    .bp3-tag.bp3-intent-warning{
      background:#d9822b;
      color:#ffffff; }
      .bp3-tag.bp3-intent-warning.bp3-interactive{
        cursor:pointer; }
        .bp3-tag.bp3-intent-warning.bp3-interactive:hover{
          background-color:rgba(217, 130, 43, 0.85); }
        .bp3-tag.bp3-intent-warning.bp3-interactive.bp3-active, .bp3-tag.bp3-intent-warning.bp3-interactive:active{
          background-color:rgba(217, 130, 43, 0.7); }
    .bp3-tag.bp3-intent-danger{
      background:#db3737;
      color:#ffffff; }
      .bp3-tag.bp3-intent-danger.bp3-interactive{
        cursor:pointer; }
        .bp3-tag.bp3-intent-danger.bp3-interactive:hover{
          background-color:rgba(219, 55, 55, 0.85); }
        .bp3-tag.bp3-intent-danger.bp3-interactive.bp3-active, .bp3-tag.bp3-intent-danger.bp3-interactive:active{
          background-color:rgba(219, 55, 55, 0.7); }
    .bp3-tag.bp3-fill{
      display:-webkit-box;
      display:-ms-flexbox;
      display:flex;
      width:100%; }
    .bp3-tag.bp3-minimal > .bp3-icon, .bp3-tag.bp3-minimal .bp3-icon-standard, .bp3-tag.bp3-minimal .bp3-icon-large{
      fill:#5c7080; }
    .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]){
      background-color:rgba(138, 155, 168, 0.2);
      color:#182026; }
      .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]).bp3-interactive{
        cursor:pointer; }
        .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]).bp3-interactive:hover{
          background-color:rgba(92, 112, 128, 0.3); }
        .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]).bp3-interactive.bp3-active, .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]).bp3-interactive:active{
          background-color:rgba(92, 112, 128, 0.4); }
      .bp3-dark .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]){
        color:#f5f8fa; }
        .bp3-dark .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]).bp3-interactive{
          cursor:pointer; }
          .bp3-dark .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]).bp3-interactive:hover{
            background-color:rgba(191, 204, 214, 0.3); }
          .bp3-dark .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]).bp3-interactive.bp3-active, .bp3-dark .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]).bp3-interactive:active{
            background-color:rgba(191, 204, 214, 0.4); }
        .bp3-dark .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]) > .bp3-icon, .bp3-dark .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]) .bp3-icon-standard, .bp3-dark .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]) .bp3-icon-large{
          fill:#a7b6c2; }
    .bp3-tag.bp3-minimal.bp3-intent-primary{
      background-color:rgba(19, 124, 189, 0.15);
      color:#106ba3; }
      .bp3-tag.bp3-minimal.bp3-intent-primary.bp3-interactive{
        cursor:pointer; }
        .bp3-tag.bp3-minimal.bp3-intent-primary.bp3-interactive:hover{
          background-color:rgba(19, 124, 189, 0.25); }
        .bp3-tag.bp3-minimal.bp3-intent-primary.bp3-interactive.bp3-active, .bp3-tag.bp3-minimal.bp3-intent-primary.bp3-interactive:active{
          background-color:rgba(19, 124, 189, 0.35); }
      .bp3-tag.bp3-minimal.bp3-intent-primary > .bp3-icon, .bp3-tag.bp3-minimal.bp3-intent-primary .bp3-icon-standard, .bp3-tag.bp3-minimal.bp3-intent-primary .bp3-icon-large{
        fill:#137cbd; }
      .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-primary{
        background-color:rgba(19, 124, 189, 0.25);
        color:#48aff0; }
        .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-primary.bp3-interactive{
          cursor:pointer; }
          .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-primary.bp3-interactive:hover{
            background-color:rgba(19, 124, 189, 0.35); }
          .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-primary.bp3-interactive.bp3-active, .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-primary.bp3-interactive:active{
            background-color:rgba(19, 124, 189, 0.45); }
    .bp3-tag.bp3-minimal.bp3-intent-success{
      background-color:rgba(15, 153, 96, 0.15);
      color:#0d8050; }
      .bp3-tag.bp3-minimal.bp3-intent-success.bp3-interactive{
        cursor:pointer; }
        .bp3-tag.bp3-minimal.bp3-intent-success.bp3-interactive:hover{
          background-color:rgba(15, 153, 96, 0.25); }
        .bp3-tag.bp3-minimal.bp3-intent-success.bp3-interactive.bp3-active, .bp3-tag.bp3-minimal.bp3-intent-success.bp3-interactive:active{
          background-color:rgba(15, 153, 96, 0.35); }
      .bp3-tag.bp3-minimal.bp3-intent-success > .bp3-icon, .bp3-tag.bp3-minimal.bp3-intent-success .bp3-icon-standard, .bp3-tag.bp3-minimal.bp3-intent-success .bp3-icon-large{
        fill:#0f9960; }
      .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-success{
        background-color:rgba(15, 153, 96, 0.25);
        color:#3dcc91; }
        .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-success.bp3-interactive{
          cursor:pointer; }
          .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-success.bp3-interactive:hover{
            background-color:rgba(15, 153, 96, 0.35); }
          .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-success.bp3-interactive.bp3-active, .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-success.bp3-interactive:active{
            background-color:rgba(15, 153, 96, 0.45); }
    .bp3-tag.bp3-minimal.bp3-intent-warning{
      background-color:rgba(217, 130, 43, 0.15);
      color:#bf7326; }
      .bp3-tag.bp3-minimal.bp3-intent-warning.bp3-interactive{
        cursor:pointer; }
        .bp3-tag.bp3-minimal.bp3-intent-warning.bp3-interactive:hover{
          background-color:rgba(217, 130, 43, 0.25); }
        .bp3-tag.bp3-minimal.bp3-intent-warning.bp3-interactive.bp3-active, .bp3-tag.bp3-minimal.bp3-intent-warning.bp3-interactive:active{
          background-color:rgba(217, 130, 43, 0.35); }
      .bp3-tag.bp3-minimal.bp3-intent-warning > .bp3-icon, .bp3-tag.bp3-minimal.bp3-intent-warning .bp3-icon-standard, .bp3-tag.bp3-minimal.bp3-intent-warning .bp3-icon-large{
        fill:#d9822b; }
      .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-warning{
        background-color:rgba(217, 130, 43, 0.25);
        color:#ffb366; }
        .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-warning.bp3-interactive{
          cursor:pointer; }
          .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-warning.bp3-interactive:hover{
            background-color:rgba(217, 130, 43, 0.35); }
          .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-warning.bp3-interactive.bp3-active, .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-warning.bp3-interactive:active{
            background-color:rgba(217, 130, 43, 0.45); }
    .bp3-tag.bp3-minimal.bp3-intent-danger{
      background-color:rgba(219, 55, 55, 0.15);
      color:#c23030; }
      .bp3-tag.bp3-minimal.bp3-intent-danger.bp3-interactive{
        cursor:pointer; }
        .bp3-tag.bp3-minimal.bp3-intent-danger.bp3-interactive:hover{
          background-color:rgba(219, 55, 55, 0.25); }
        .bp3-tag.bp3-minimal.bp3-intent-danger.bp3-interactive.bp3-active, .bp3-tag.bp3-minimal.bp3-intent-danger.bp3-interactive:active{
          background-color:rgba(219, 55, 55, 0.35); }
      .bp3-tag.bp3-minimal.bp3-intent-danger > .bp3-icon, .bp3-tag.bp3-minimal.bp3-intent-danger .bp3-icon-standard, .bp3-tag.bp3-minimal.bp3-intent-danger .bp3-icon-large{
        fill:#db3737; }
      .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-danger{
        background-color:rgba(219, 55, 55, 0.25);
        color:#ff7373; }
        .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-danger.bp3-interactive{
          cursor:pointer; }
          .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-danger.bp3-interactive:hover{
            background-color:rgba(219, 55, 55, 0.35); }
          .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-danger.bp3-interactive.bp3-active, .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-danger.bp3-interactive:active{
            background-color:rgba(219, 55, 55, 0.45); }

  .bp3-tag-remove{
    background:none;
    border:none;
    color:inherit;
    cursor:pointer;
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    margin-bottom:-2px;
    margin-right:-6px !important;
    margin-top:-2px;
    opacity:0.5;
    padding:2px;
    padding-left:0; }
    .bp3-tag-remove:hover{
      background:none;
      opacity:0.8;
      text-decoration:none; }
    .bp3-tag-remove:active{
      opacity:1; }
    .bp3-tag-remove:empty::before{
      font-family:"Icons16", sans-serif;
      font-size:16px;
      font-style:normal;
      font-weight:400;
      line-height:1;
      -moz-osx-font-smoothing:grayscale;
      -webkit-font-smoothing:antialiased;
      content:""; }
    .bp3-large .bp3-tag-remove{
      margin-right:-10px !important;
      padding:0 5px 0 0; }
      .bp3-large .bp3-tag-remove:empty::before{
        font-family:"Icons20", sans-serif;
        font-size:20px;
        font-style:normal;
        font-weight:400;
        line-height:1; }
  .bp3-tag-input{
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    -webkit-box-orient:horizontal;
    -webkit-box-direction:normal;
        -ms-flex-direction:row;
            flex-direction:row;
    -webkit-box-align:start;
        -ms-flex-align:start;
            align-items:flex-start;
    cursor:text;
    height:auto;
    line-height:inherit;
    min-height:30px;
    padding-left:5px;
    padding-right:0; }
    .bp3-tag-input > *{
      -webkit-box-flex:0;
          -ms-flex-positive:0;
              flex-grow:0;
      -ms-flex-negative:0;
          flex-shrink:0; }
    .bp3-tag-input > .bp3-tag-input-values{
      -webkit-box-flex:1;
          -ms-flex-positive:1;
              flex-grow:1;
      -ms-flex-negative:1;
          flex-shrink:1; }
    .bp3-tag-input .bp3-tag-input-icon{
      color:#5c7080;
      margin-left:2px;
      margin-right:7px;
      margin-top:7px; }
    .bp3-tag-input .bp3-tag-input-values{
      display:-webkit-box;
      display:-ms-flexbox;
      display:flex;
      -webkit-box-orient:horizontal;
      -webkit-box-direction:normal;
          -ms-flex-direction:row;
              flex-direction:row;
      -webkit-box-align:center;
          -ms-flex-align:center;
              align-items:center;
      -ms-flex-item-align:stretch;
          align-self:stretch;
      -ms-flex-wrap:wrap;
          flex-wrap:wrap;
      margin-right:7px;
      margin-top:5px;
      min-width:0; }
      .bp3-tag-input .bp3-tag-input-values > *{
        -webkit-box-flex:0;
            -ms-flex-positive:0;
                flex-grow:0;
        -ms-flex-negative:0;
            flex-shrink:0; }
      .bp3-tag-input .bp3-tag-input-values > .bp3-fill{
        -webkit-box-flex:1;
            -ms-flex-positive:1;
                flex-grow:1;
        -ms-flex-negative:1;
            flex-shrink:1; }
      .bp3-tag-input .bp3-tag-input-values::before,
      .bp3-tag-input .bp3-tag-input-values > *{
        margin-right:5px; }
      .bp3-tag-input .bp3-tag-input-values:empty::before,
      .bp3-tag-input .bp3-tag-input-values > :last-child{
        margin-right:0; }
      .bp3-tag-input .bp3-tag-input-values:first-child .bp3-input-ghost:first-child{
        padding-left:5px; }
      .bp3-tag-input .bp3-tag-input-values > *{
        margin-bottom:5px; }
    .bp3-tag-input .bp3-tag{
      overflow-wrap:break-word; }
      .bp3-tag-input .bp3-tag.bp3-active{
        outline:rgba(19, 124, 189, 0.6) auto 2px;
        outline-offset:0;
        -moz-outline-radius:6px; }
    .bp3-tag-input .bp3-input-ghost{
      -webkit-box-flex:1;
          -ms-flex:1 1 auto;
              flex:1 1 auto;
      line-height:20px;
      width:80px; }
      .bp3-tag-input .bp3-input-ghost:disabled, .bp3-tag-input .bp3-input-ghost.bp3-disabled{
        cursor:not-allowed; }
    .bp3-tag-input .bp3-button,
    .bp3-tag-input .bp3-spinner{
      margin:3px;
      margin-left:0; }
    .bp3-tag-input .bp3-button{
      min-height:24px;
      min-width:24px;
      padding:0 7px; }
    .bp3-tag-input.bp3-large{
      height:auto;
      min-height:40px; }
      .bp3-tag-input.bp3-large::before,
      .bp3-tag-input.bp3-large > *{
        margin-right:10px; }
      .bp3-tag-input.bp3-large:empty::before,
      .bp3-tag-input.bp3-large > :last-child{
        margin-right:0; }
      .bp3-tag-input.bp3-large .bp3-tag-input-icon{
        margin-left:5px;
        margin-top:10px; }
      .bp3-tag-input.bp3-large .bp3-input-ghost{
        line-height:30px; }
      .bp3-tag-input.bp3-large .bp3-button{
        min-height:30px;
        min-width:30px;
        padding:5px 10px;
        margin:5px;
        margin-left:0; }
      .bp3-tag-input.bp3-large .bp3-spinner{
        margin:8px;
        margin-left:0; }
    .bp3-tag-input.bp3-active{
      background-color:#ffffff;
      -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
      .bp3-tag-input.bp3-active.bp3-intent-primary{
        -webkit-box-shadow:0 0 0 1px #106ba3, 0 0 0 3px rgba(16, 107, 163, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
                box-shadow:0 0 0 1px #106ba3, 0 0 0 3px rgba(16, 107, 163, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
      .bp3-tag-input.bp3-active.bp3-intent-success{
        -webkit-box-shadow:0 0 0 1px #0d8050, 0 0 0 3px rgba(13, 128, 80, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
                box-shadow:0 0 0 1px #0d8050, 0 0 0 3px rgba(13, 128, 80, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
      .bp3-tag-input.bp3-active.bp3-intent-warning{
        -webkit-box-shadow:0 0 0 1px #bf7326, 0 0 0 3px rgba(191, 115, 38, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
                box-shadow:0 0 0 1px #bf7326, 0 0 0 3px rgba(191, 115, 38, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
      .bp3-tag-input.bp3-active.bp3-intent-danger{
        -webkit-box-shadow:0 0 0 1px #c23030, 0 0 0 3px rgba(194, 48, 48, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
                box-shadow:0 0 0 1px #c23030, 0 0 0 3px rgba(194, 48, 48, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-dark .bp3-tag-input .bp3-tag-input-icon, .bp3-tag-input.bp3-dark .bp3-tag-input-icon{
      color:#a7b6c2; }
    .bp3-dark .bp3-tag-input .bp3-input-ghost, .bp3-tag-input.bp3-dark .bp3-input-ghost{
      color:#f5f8fa; }
      .bp3-dark .bp3-tag-input .bp3-input-ghost::-webkit-input-placeholder, .bp3-tag-input.bp3-dark .bp3-input-ghost::-webkit-input-placeholder{
        color:rgba(167, 182, 194, 0.6); }
      .bp3-dark .bp3-tag-input .bp3-input-ghost::-moz-placeholder, .bp3-tag-input.bp3-dark .bp3-input-ghost::-moz-placeholder{
        color:rgba(167, 182, 194, 0.6); }
      .bp3-dark .bp3-tag-input .bp3-input-ghost:-ms-input-placeholder, .bp3-tag-input.bp3-dark .bp3-input-ghost:-ms-input-placeholder{
        color:rgba(167, 182, 194, 0.6); }
      .bp3-dark .bp3-tag-input .bp3-input-ghost::-ms-input-placeholder, .bp3-tag-input.bp3-dark .bp3-input-ghost::-ms-input-placeholder{
        color:rgba(167, 182, 194, 0.6); }
      .bp3-dark .bp3-tag-input .bp3-input-ghost::placeholder, .bp3-tag-input.bp3-dark .bp3-input-ghost::placeholder{
        color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-tag-input.bp3-active, .bp3-tag-input.bp3-dark.bp3-active{
      background-color:rgba(16, 22, 26, 0.3);
      -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-tag-input.bp3-active.bp3-intent-primary, .bp3-tag-input.bp3-dark.bp3-active.bp3-intent-primary{
        -webkit-box-shadow:0 0 0 1px #106ba3, 0 0 0 3px rgba(16, 107, 163, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
                box-shadow:0 0 0 1px #106ba3, 0 0 0 3px rgba(16, 107, 163, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-tag-input.bp3-active.bp3-intent-success, .bp3-tag-input.bp3-dark.bp3-active.bp3-intent-success{
        -webkit-box-shadow:0 0 0 1px #0d8050, 0 0 0 3px rgba(13, 128, 80, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
                box-shadow:0 0 0 1px #0d8050, 0 0 0 3px rgba(13, 128, 80, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-tag-input.bp3-active.bp3-intent-warning, .bp3-tag-input.bp3-dark.bp3-active.bp3-intent-warning{
        -webkit-box-shadow:0 0 0 1px #bf7326, 0 0 0 3px rgba(191, 115, 38, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
                box-shadow:0 0 0 1px #bf7326, 0 0 0 3px rgba(191, 115, 38, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-tag-input.bp3-active.bp3-intent-danger, .bp3-tag-input.bp3-dark.bp3-active.bp3-intent-danger{
        -webkit-box-shadow:0 0 0 1px #c23030, 0 0 0 3px rgba(194, 48, 48, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
                box-shadow:0 0 0 1px #c23030, 0 0 0 3px rgba(194, 48, 48, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }

  .bp3-input-ghost{
    background:none;
    border:none;
    -webkit-box-shadow:none;
            box-shadow:none;
    padding:0; }
    .bp3-input-ghost::-webkit-input-placeholder{
      color:rgba(92, 112, 128, 0.6);
      opacity:1; }
    .bp3-input-ghost::-moz-placeholder{
      color:rgba(92, 112, 128, 0.6);
      opacity:1; }
    .bp3-input-ghost:-ms-input-placeholder{
      color:rgba(92, 112, 128, 0.6);
      opacity:1; }
    .bp3-input-ghost::-ms-input-placeholder{
      color:rgba(92, 112, 128, 0.6);
      opacity:1; }
    .bp3-input-ghost::placeholder{
      color:rgba(92, 112, 128, 0.6);
      opacity:1; }
    .bp3-input-ghost:focus{
      outline:none !important; }
  .bp3-toast{
    -webkit-box-align:start;
        -ms-flex-align:start;
            align-items:flex-start;
    background-color:#ffffff;
    border-radius:3px;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    margin:20px 0 0;
    max-width:500px;
    min-width:300px;
    pointer-events:all;
    position:relative !important; }
    .bp3-toast.bp3-toast-enter, .bp3-toast.bp3-toast-appear{
      -webkit-transform:translateY(-40px);
              transform:translateY(-40px); }
    .bp3-toast.bp3-toast-enter-active, .bp3-toast.bp3-toast-appear-active{
      -webkit-transform:translateY(0);
              transform:translateY(0);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:300ms;
              transition-duration:300ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11);
              transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11); }
    .bp3-toast.bp3-toast-enter ~ .bp3-toast, .bp3-toast.bp3-toast-appear ~ .bp3-toast{
      -webkit-transform:translateY(-40px);
              transform:translateY(-40px); }
    .bp3-toast.bp3-toast-enter-active ~ .bp3-toast, .bp3-toast.bp3-toast-appear-active ~ .bp3-toast{
      -webkit-transform:translateY(0);
              transform:translateY(0);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:300ms;
              transition-duration:300ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11);
              transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11); }
    .bp3-toast.bp3-toast-exit{
      opacity:1;
      -webkit-filter:blur(0);
              filter:blur(0); }
    .bp3-toast.bp3-toast-exit-active{
      opacity:0;
      -webkit-filter:blur(10px);
              filter:blur(10px);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:300ms;
              transition-duration:300ms;
      -webkit-transition-property:opacity, -webkit-filter;
      transition-property:opacity, -webkit-filter;
      transition-property:opacity, filter;
      transition-property:opacity, filter, -webkit-filter;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-toast.bp3-toast-exit ~ .bp3-toast{
      -webkit-transform:translateY(0);
              transform:translateY(0); }
    .bp3-toast.bp3-toast-exit-active ~ .bp3-toast{
      -webkit-transform:translateY(-40px);
              transform:translateY(-40px);
      -webkit-transition-delay:50ms;
              transition-delay:50ms;
      -webkit-transition-duration:100ms;
              transition-duration:100ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-toast .bp3-button-group{
      -webkit-box-flex:0;
          -ms-flex:0 0 auto;
              flex:0 0 auto;
      padding:5px;
      padding-left:0; }
    .bp3-toast > .bp3-icon{
      color:#5c7080;
      margin:12px;
      margin-right:0; }
    .bp3-toast.bp3-dark,
    .bp3-dark .bp3-toast{
      background-color:#394b59;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4); }
      .bp3-toast.bp3-dark > .bp3-icon,
      .bp3-dark .bp3-toast > .bp3-icon{
        color:#a7b6c2; }
    .bp3-toast[class*="bp3-intent-"] a{
      color:rgba(255, 255, 255, 0.7); }
      .bp3-toast[class*="bp3-intent-"] a:hover{
        color:#ffffff; }
    .bp3-toast[class*="bp3-intent-"] > .bp3-icon{
      color:#ffffff; }
    .bp3-toast[class*="bp3-intent-"] .bp3-button, .bp3-toast[class*="bp3-intent-"] .bp3-button::before,
    .bp3-toast[class*="bp3-intent-"] .bp3-button .bp3-icon, .bp3-toast[class*="bp3-intent-"] .bp3-button:active{
      color:rgba(255, 255, 255, 0.7) !important; }
    .bp3-toast[class*="bp3-intent-"] .bp3-button:focus{
      outline-color:rgba(255, 255, 255, 0.5); }
    .bp3-toast[class*="bp3-intent-"] .bp3-button:hover{
      background-color:rgba(255, 255, 255, 0.15) !important;
      color:#ffffff !important; }
    .bp3-toast[class*="bp3-intent-"] .bp3-button:active{
      background-color:rgba(255, 255, 255, 0.3) !important;
      color:#ffffff !important; }
    .bp3-toast[class*="bp3-intent-"] .bp3-button::after{
      background:rgba(255, 255, 255, 0.3) !important; }
    .bp3-toast.bp3-intent-primary{
      background-color:#137cbd;
      color:#ffffff; }
    .bp3-toast.bp3-intent-success{
      background-color:#0f9960;
      color:#ffffff; }
    .bp3-toast.bp3-intent-warning{
      background-color:#d9822b;
      color:#ffffff; }
    .bp3-toast.bp3-intent-danger{
      background-color:#db3737;
      color:#ffffff; }

  .bp3-toast-message{
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto;
    padding:11px;
    word-break:break-word; }

  .bp3-toast-container{
    -webkit-box-align:center;
        -ms-flex-align:center;
            align-items:center;
    display:-webkit-box !important;
    display:-ms-flexbox !important;
    display:flex !important;
    -webkit-box-orient:vertical;
    -webkit-box-direction:normal;
        -ms-flex-direction:column;
            flex-direction:column;
    left:0;
    overflow:hidden;
    padding:0 20px 20px;
    pointer-events:none;
    position:fixed;
    right:0;
    z-index:40; }
    .bp3-toast-container.bp3-toast-container-top{
      top:0; }
    .bp3-toast-container.bp3-toast-container-bottom{
      bottom:0;
      -webkit-box-orient:vertical;
      -webkit-box-direction:reverse;
          -ms-flex-direction:column-reverse;
              flex-direction:column-reverse;
      top:auto; }
    .bp3-toast-container.bp3-toast-container-left{
      -webkit-box-align:start;
          -ms-flex-align:start;
              align-items:flex-start; }
    .bp3-toast-container.bp3-toast-container-right{
      -webkit-box-align:end;
          -ms-flex-align:end;
              align-items:flex-end; }

  .bp3-toast-container-bottom .bp3-toast.bp3-toast-enter:not(.bp3-toast-enter-active),
  .bp3-toast-container-bottom .bp3-toast.bp3-toast-enter:not(.bp3-toast-enter-active) ~ .bp3-toast, .bp3-toast-container-bottom .bp3-toast.bp3-toast-appear:not(.bp3-toast-appear-active),
  .bp3-toast-container-bottom .bp3-toast.bp3-toast-appear:not(.bp3-toast-appear-active) ~ .bp3-toast,
  .bp3-toast-container-bottom .bp3-toast.bp3-toast-exit-active ~ .bp3-toast,
  .bp3-toast-container-bottom .bp3-toast.bp3-toast-leave-active ~ .bp3-toast{
    -webkit-transform:translateY(60px);
            transform:translateY(60px); }
  .bp3-tooltip{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
    -webkit-transform:scale(1);
            transform:scale(1); }
    .bp3-tooltip .bp3-popover-arrow{
      height:22px;
      position:absolute;
      width:22px; }
      .bp3-tooltip .bp3-popover-arrow::before{
        height:14px;
        margin:4px;
        width:14px; }
    .bp3-tether-element-attached-bottom.bp3-tether-target-attached-top > .bp3-tooltip{
      margin-bottom:11px;
      margin-top:-11px; }
      .bp3-tether-element-attached-bottom.bp3-tether-target-attached-top > .bp3-tooltip > .bp3-popover-arrow{
        bottom:-8px; }
        .bp3-tether-element-attached-bottom.bp3-tether-target-attached-top > .bp3-tooltip > .bp3-popover-arrow svg{
          -webkit-transform:rotate(-90deg);
                  transform:rotate(-90deg); }
    .bp3-tether-element-attached-left.bp3-tether-target-attached-right > .bp3-tooltip{
      margin-left:11px; }
      .bp3-tether-element-attached-left.bp3-tether-target-attached-right > .bp3-tooltip > .bp3-popover-arrow{
        left:-8px; }
        .bp3-tether-element-attached-left.bp3-tether-target-attached-right > .bp3-tooltip > .bp3-popover-arrow svg{
          -webkit-transform:rotate(0);
                  transform:rotate(0); }
    .bp3-tether-element-attached-top.bp3-tether-target-attached-bottom > .bp3-tooltip{
      margin-top:11px; }
      .bp3-tether-element-attached-top.bp3-tether-target-attached-bottom > .bp3-tooltip > .bp3-popover-arrow{
        top:-8px; }
        .bp3-tether-element-attached-top.bp3-tether-target-attached-bottom > .bp3-tooltip > .bp3-popover-arrow svg{
          -webkit-transform:rotate(90deg);
                  transform:rotate(90deg); }
    .bp3-tether-element-attached-right.bp3-tether-target-attached-left > .bp3-tooltip{
      margin-left:-11px;
      margin-right:11px; }
      .bp3-tether-element-attached-right.bp3-tether-target-attached-left > .bp3-tooltip > .bp3-popover-arrow{
        right:-8px; }
        .bp3-tether-element-attached-right.bp3-tether-target-attached-left > .bp3-tooltip > .bp3-popover-arrow svg{
          -webkit-transform:rotate(180deg);
                  transform:rotate(180deg); }
    .bp3-tether-element-attached-middle > .bp3-tooltip > .bp3-popover-arrow{
      top:50%;
      -webkit-transform:translateY(-50%);
              transform:translateY(-50%); }
    .bp3-tether-element-attached-center > .bp3-tooltip > .bp3-popover-arrow{
      right:50%;
      -webkit-transform:translateX(50%);
              transform:translateX(50%); }
    .bp3-tether-element-attached-top.bp3-tether-target-attached-top > .bp3-tooltip > .bp3-popover-arrow{
      top:-0.22183px; }
    .bp3-tether-element-attached-right.bp3-tether-target-attached-right > .bp3-tooltip > .bp3-popover-arrow{
      right:-0.22183px; }
    .bp3-tether-element-attached-left.bp3-tether-target-attached-left > .bp3-tooltip > .bp3-popover-arrow{
      left:-0.22183px; }
    .bp3-tether-element-attached-bottom.bp3-tether-target-attached-bottom > .bp3-tooltip > .bp3-popover-arrow{
      bottom:-0.22183px; }
    .bp3-tether-element-attached-top.bp3-tether-element-attached-left > .bp3-tooltip{
      -webkit-transform-origin:top left;
              transform-origin:top left; }
    .bp3-tether-element-attached-top.bp3-tether-element-attached-center > .bp3-tooltip{
      -webkit-transform-origin:top center;
              transform-origin:top center; }
    .bp3-tether-element-attached-top.bp3-tether-element-attached-right > .bp3-tooltip{
      -webkit-transform-origin:top right;
              transform-origin:top right; }
    .bp3-tether-element-attached-middle.bp3-tether-element-attached-left > .bp3-tooltip{
      -webkit-transform-origin:center left;
              transform-origin:center left; }
    .bp3-tether-element-attached-middle.bp3-tether-element-attached-center > .bp3-tooltip{
      -webkit-transform-origin:center center;
              transform-origin:center center; }
    .bp3-tether-element-attached-middle.bp3-tether-element-attached-right > .bp3-tooltip{
      -webkit-transform-origin:center right;
              transform-origin:center right; }
    .bp3-tether-element-attached-bottom.bp3-tether-element-attached-left > .bp3-tooltip{
      -webkit-transform-origin:bottom left;
              transform-origin:bottom left; }
    .bp3-tether-element-attached-bottom.bp3-tether-element-attached-center > .bp3-tooltip{
      -webkit-transform-origin:bottom center;
              transform-origin:bottom center; }
    .bp3-tether-element-attached-bottom.bp3-tether-element-attached-right > .bp3-tooltip{
      -webkit-transform-origin:bottom right;
              transform-origin:bottom right; }
    .bp3-tooltip .bp3-popover-content{
      background:#394b59;
      color:#f5f8fa; }
    .bp3-tooltip .bp3-popover-arrow::before{
      -webkit-box-shadow:1px 1px 6px rgba(16, 22, 26, 0.2);
              box-shadow:1px 1px 6px rgba(16, 22, 26, 0.2); }
    .bp3-tooltip .bp3-popover-arrow-border{
      fill:#10161a;
      fill-opacity:0.1; }
    .bp3-tooltip .bp3-popover-arrow-fill{
      fill:#394b59; }
    .bp3-popover-enter > .bp3-tooltip, .bp3-popover-appear > .bp3-tooltip{
      -webkit-transform:scale(0.8);
              transform:scale(0.8); }
    .bp3-popover-enter-active > .bp3-tooltip, .bp3-popover-appear-active > .bp3-tooltip{
      -webkit-transform:scale(1);
              transform:scale(1);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:100ms;
              transition-duration:100ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-popover-exit > .bp3-tooltip{
      -webkit-transform:scale(1);
              transform:scale(1); }
    .bp3-popover-exit-active > .bp3-tooltip{
      -webkit-transform:scale(0.8);
              transform:scale(0.8);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:100ms;
              transition-duration:100ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-tooltip .bp3-popover-content{
      padding:10px 12px; }
    .bp3-tooltip.bp3-dark,
    .bp3-dark .bp3-tooltip{
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4); }
      .bp3-tooltip.bp3-dark .bp3-popover-content,
      .bp3-dark .bp3-tooltip .bp3-popover-content{
        background:#e1e8ed;
        color:#394b59; }
      .bp3-tooltip.bp3-dark .bp3-popover-arrow::before,
      .bp3-dark .bp3-tooltip .bp3-popover-arrow::before{
        -webkit-box-shadow:1px 1px 6px rgba(16, 22, 26, 0.4);
                box-shadow:1px 1px 6px rgba(16, 22, 26, 0.4); }
      .bp3-tooltip.bp3-dark .bp3-popover-arrow-border,
      .bp3-dark .bp3-tooltip .bp3-popover-arrow-border{
        fill:#10161a;
        fill-opacity:0.2; }
      .bp3-tooltip.bp3-dark .bp3-popover-arrow-fill,
      .bp3-dark .bp3-tooltip .bp3-popover-arrow-fill{
        fill:#e1e8ed; }
    .bp3-tooltip.bp3-intent-primary .bp3-popover-content{
      background:#137cbd;
      color:#ffffff; }
    .bp3-tooltip.bp3-intent-primary .bp3-popover-arrow-fill{
      fill:#137cbd; }
    .bp3-tooltip.bp3-intent-success .bp3-popover-content{
      background:#0f9960;
      color:#ffffff; }
    .bp3-tooltip.bp3-intent-success .bp3-popover-arrow-fill{
      fill:#0f9960; }
    .bp3-tooltip.bp3-intent-warning .bp3-popover-content{
      background:#d9822b;
      color:#ffffff; }
    .bp3-tooltip.bp3-intent-warning .bp3-popover-arrow-fill{
      fill:#d9822b; }
    .bp3-tooltip.bp3-intent-danger .bp3-popover-content{
      background:#db3737;
      color:#ffffff; }
    .bp3-tooltip.bp3-intent-danger .bp3-popover-arrow-fill{
      fill:#db3737; }

  .bp3-tooltip-indicator{
    border-bottom:dotted 1px;
    cursor:help; }
  .bp3-tree .bp3-icon, .bp3-tree .bp3-icon-standard, .bp3-tree .bp3-icon-large{
    color:#5c7080; }
    .bp3-tree .bp3-icon.bp3-intent-primary, .bp3-tree .bp3-icon-standard.bp3-intent-primary, .bp3-tree .bp3-icon-large.bp3-intent-primary{
      color:#137cbd; }
    .bp3-tree .bp3-icon.bp3-intent-success, .bp3-tree .bp3-icon-standard.bp3-intent-success, .bp3-tree .bp3-icon-large.bp3-intent-success{
      color:#0f9960; }
    .bp3-tree .bp3-icon.bp3-intent-warning, .bp3-tree .bp3-icon-standard.bp3-intent-warning, .bp3-tree .bp3-icon-large.bp3-intent-warning{
      color:#d9822b; }
    .bp3-tree .bp3-icon.bp3-intent-danger, .bp3-tree .bp3-icon-standard.bp3-intent-danger, .bp3-tree .bp3-icon-large.bp3-intent-danger{
      color:#db3737; }

  .bp3-tree-node-list{
    list-style:none;
    margin:0;
    padding-left:0; }

  .bp3-tree-root{
    background-color:transparent;
    cursor:default;
    padding-left:0;
    position:relative; }

  .bp3-tree-node-content-0{
    padding-left:0px; }

  .bp3-tree-node-content-1{
    padding-left:23px; }

  .bp3-tree-node-content-2{
    padding-left:46px; }

  .bp3-tree-node-content-3{
    padding-left:69px; }

  .bp3-tree-node-content-4{
    padding-left:92px; }

  .bp3-tree-node-content-5{
    padding-left:115px; }

  .bp3-tree-node-content-6{
    padding-left:138px; }

  .bp3-tree-node-content-7{
    padding-left:161px; }

  .bp3-tree-node-content-8{
    padding-left:184px; }

  .bp3-tree-node-content-9{
    padding-left:207px; }

  .bp3-tree-node-content-10{
    padding-left:230px; }

  .bp3-tree-node-content-11{
    padding-left:253px; }

  .bp3-tree-node-content-12{
    padding-left:276px; }

  .bp3-tree-node-content-13{
    padding-left:299px; }

  .bp3-tree-node-content-14{
    padding-left:322px; }

  .bp3-tree-node-content-15{
    padding-left:345px; }

  .bp3-tree-node-content-16{
    padding-left:368px; }

  .bp3-tree-node-content-17{
    padding-left:391px; }

  .bp3-tree-node-content-18{
    padding-left:414px; }

  .bp3-tree-node-content-19{
    padding-left:437px; }

  .bp3-tree-node-content-20{
    padding-left:460px; }

  .bp3-tree-node-content{
    -webkit-box-align:center;
        -ms-flex-align:center;
            align-items:center;
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    height:30px;
    padding-right:5px;
    width:100%; }
    .bp3-tree-node-content:hover{
      background-color:rgba(191, 204, 214, 0.4); }

  .bp3-tree-node-caret,
  .bp3-tree-node-caret-none{
    min-width:30px; }

  .bp3-tree-node-caret{
    color:#5c7080;
    cursor:pointer;
    padding:7px;
    -webkit-transform:rotate(0deg);
            transform:rotate(0deg);
    -webkit-transition:-webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:-webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-tree-node-caret:hover{
      color:#182026; }
    .bp3-dark .bp3-tree-node-caret{
      color:#a7b6c2; }
      .bp3-dark .bp3-tree-node-caret:hover{
        color:#f5f8fa; }
    .bp3-tree-node-caret.bp3-tree-node-caret-open{
      -webkit-transform:rotate(90deg);
              transform:rotate(90deg); }
    .bp3-tree-node-caret.bp3-icon-standard::before{
      content:""; }

  .bp3-tree-node-icon{
    margin-right:7px;
    position:relative; }

  .bp3-tree-node-label{
    overflow:hidden;
    text-overflow:ellipsis;
    white-space:nowrap;
    word-wrap:normal;
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto;
    position:relative;
    -webkit-user-select:none;
      -moz-user-select:none;
        -ms-user-select:none;
            user-select:none; }
    .bp3-tree-node-label span{
      display:inline; }

  .bp3-tree-node-secondary-label{
    padding:0 5px;
    -webkit-user-select:none;
      -moz-user-select:none;
        -ms-user-select:none;
            user-select:none; }
    .bp3-tree-node-secondary-label .bp3-popover-wrapper,
    .bp3-tree-node-secondary-label .bp3-popover-target{
      -webkit-box-align:center;
          -ms-flex-align:center;
              align-items:center;
      display:-webkit-box;
      display:-ms-flexbox;
      display:flex; }

  .bp3-tree-node.bp3-disabled .bp3-tree-node-content{
    background-color:inherit;
    color:rgba(92, 112, 128, 0.6);
    cursor:not-allowed; }

  .bp3-tree-node.bp3-disabled .bp3-tree-node-caret,
  .bp3-tree-node.bp3-disabled .bp3-tree-node-icon{
    color:rgba(92, 112, 128, 0.6);
    cursor:not-allowed; }

  .bp3-tree-node.bp3-tree-node-selected > .bp3-tree-node-content{
    background-color:#137cbd; }
    .bp3-tree-node.bp3-tree-node-selected > .bp3-tree-node-content,
    .bp3-tree-node.bp3-tree-node-selected > .bp3-tree-node-content .bp3-icon, .bp3-tree-node.bp3-tree-node-selected > .bp3-tree-node-content .bp3-icon-standard, .bp3-tree-node.bp3-tree-node-selected > .bp3-tree-node-content .bp3-icon-large{
      color:#ffffff; }
    .bp3-tree-node.bp3-tree-node-selected > .bp3-tree-node-content .bp3-tree-node-caret::before{
      color:rgba(255, 255, 255, 0.7); }
    .bp3-tree-node.bp3-tree-node-selected > .bp3-tree-node-content .bp3-tree-node-caret:hover::before{
      color:#ffffff; }

  .bp3-dark .bp3-tree-node-content:hover{
    background-color:rgba(92, 112, 128, 0.3); }

  .bp3-dark .bp3-tree .bp3-icon, .bp3-dark .bp3-tree .bp3-icon-standard, .bp3-dark .bp3-tree .bp3-icon-large{
    color:#a7b6c2; }
    .bp3-dark .bp3-tree .bp3-icon.bp3-intent-primary, .bp3-dark .bp3-tree .bp3-icon-standard.bp3-intent-primary, .bp3-dark .bp3-tree .bp3-icon-large.bp3-intent-primary{
      color:#137cbd; }
    .bp3-dark .bp3-tree .bp3-icon.bp3-intent-success, .bp3-dark .bp3-tree .bp3-icon-standard.bp3-intent-success, .bp3-dark .bp3-tree .bp3-icon-large.bp3-intent-success{
      color:#0f9960; }
    .bp3-dark .bp3-tree .bp3-icon.bp3-intent-warning, .bp3-dark .bp3-tree .bp3-icon-standard.bp3-intent-warning, .bp3-dark .bp3-tree .bp3-icon-large.bp3-intent-warning{
      color:#d9822b; }
    .bp3-dark .bp3-tree .bp3-icon.bp3-intent-danger, .bp3-dark .bp3-tree .bp3-icon-standard.bp3-intent-danger, .bp3-dark .bp3-tree .bp3-icon-large.bp3-intent-danger{
      color:#db3737; }

  .bp3-dark .bp3-tree-node.bp3-tree-node-selected > .bp3-tree-node-content{
    background-color:#137cbd; }
  .bp3-omnibar{
    -webkit-filter:blur(0);
            filter:blur(0);
    opacity:1;
    background-color:#ffffff;
    border-radius:3px;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 4px 8px rgba(16, 22, 26, 0.2), 0 18px 46px 6px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 4px 8px rgba(16, 22, 26, 0.2), 0 18px 46px 6px rgba(16, 22, 26, 0.2);
    left:calc(50% - 250px);
    top:20vh;
    width:500px;
    z-index:21; }
    .bp3-omnibar.bp3-overlay-enter, .bp3-omnibar.bp3-overlay-appear{
      -webkit-filter:blur(20px);
              filter:blur(20px);
      opacity:0.2; }
    .bp3-omnibar.bp3-overlay-enter-active, .bp3-omnibar.bp3-overlay-appear-active{
      -webkit-filter:blur(0);
              filter:blur(0);
      opacity:1;
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:200ms;
              transition-duration:200ms;
      -webkit-transition-property:opacity, -webkit-filter;
      transition-property:opacity, -webkit-filter;
      transition-property:filter, opacity;
      transition-property:filter, opacity, -webkit-filter;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-omnibar.bp3-overlay-exit{
      -webkit-filter:blur(0);
              filter:blur(0);
      opacity:1; }
    .bp3-omnibar.bp3-overlay-exit-active{
      -webkit-filter:blur(20px);
              filter:blur(20px);
      opacity:0.2;
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:200ms;
              transition-duration:200ms;
      -webkit-transition-property:opacity, -webkit-filter;
      transition-property:opacity, -webkit-filter;
      transition-property:filter, opacity;
      transition-property:filter, opacity, -webkit-filter;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-omnibar .bp3-input{
      background-color:transparent;
      border-radius:0; }
      .bp3-omnibar .bp3-input, .bp3-omnibar .bp3-input:focus{
        -webkit-box-shadow:none;
                box-shadow:none; }
    .bp3-omnibar .bp3-menu{
      background-color:transparent;
      border-radius:0;
      -webkit-box-shadow:inset 0 1px 0 rgba(16, 22, 26, 0.15);
              box-shadow:inset 0 1px 0 rgba(16, 22, 26, 0.15);
      max-height:calc(60vh - 40px);
      overflow:auto; }
      .bp3-omnibar .bp3-menu:empty{
        display:none; }
    .bp3-dark .bp3-omnibar, .bp3-omnibar.bp3-dark{
      background-color:#30404d;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 4px 8px rgba(16, 22, 26, 0.4), 0 18px 46px 6px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 4px 8px rgba(16, 22, 26, 0.4), 0 18px 46px 6px rgba(16, 22, 26, 0.4); }

  .bp3-omnibar-overlay .bp3-overlay-backdrop{
    background-color:rgba(16, 22, 26, 0.2); }

  .bp3-select-popover .bp3-popover-content{
    padding:5px; }

  .bp3-select-popover .bp3-input-group{
    margin-bottom:0; }

  .bp3-select-popover .bp3-menu{
    max-height:300px;
    max-width:400px;
    overflow:auto;
    padding:0; }
    .bp3-select-popover .bp3-menu:not(:first-child){
      padding-top:5px; }

  .bp3-multi-select{
    min-width:150px; }

  .bp3-multi-select-popover .bp3-menu{
    max-height:300px;
    max-width:400px;
    overflow:auto; }

  .bp3-select-popover .bp3-popover-content{
    padding:5px; }

  .bp3-select-popover .bp3-input-group{
    margin-bottom:0; }

  .bp3-select-popover .bp3-menu{
    max-height:300px;
    max-width:400px;
    overflow:auto;
    padding:0; }
    .bp3-select-popover .bp3-menu:not(:first-child){
      padding-top:5px; }
  /*-----------------------------------------------------------------------------
  | Copyright (c) Jupyter Development Team.
  | Distributed under the terms of the Modified BSD License.
  |----------------------------------------------------------------------------*/

  /* This file was auto-generated by ensureUiComponents() in @jupyterlab/buildutils */

  /**
  * (DEPRECATED) Support for consuming icons as CSS background images
  */

  /* Icons urls */

  :root {
    --jp-icon-add: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTE5IDEzaC02djZoLTJ2LTZINXYtMmg2VjVoMnY2aDZ2MnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
    --jp-icon-bug: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTIwIDhoLTIuODFjLS40NS0uNzgtMS4wNy0xLjQ1LTEuODItMS45NkwxNyA0LjQxIDE1LjU5IDNsLTIuMTcgMi4xN0MxMi45NiA1LjA2IDEyLjQ5IDUgMTIgNWMtLjQ5IDAtLjk2LjA2LTEuNDEuMTdMOC40MSAzIDcgNC40MWwxLjYyIDEuNjNDNy44OCA2LjU1IDcuMjYgNy4yMiA2LjgxIDhINHYyaDIuMDljLS4wNS4zMy0uMDkuNjYtLjA5IDF2MUg0djJoMnYxYzAgLjM0LjA0LjY3LjA5IDFINHYyaDIuODFjMS4wNCAxLjc5IDIuOTcgMyA1LjE5IDNzNC4xNS0xLjIxIDUuMTktM0gyMHYtMmgtMi4wOWMuMDUtLjMzLjA5LS42Ni4wOS0xdi0xaDJ2LTJoLTJ2LTFjMC0uMzQtLjA0LS42Ny0uMDktMUgyMFY4em0tNiA4aC00di0yaDR2MnptMC00aC00di0yaDR2MnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
    --jp-icon-build: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIHZpZXdCb3g9IjAgMCAyNCAyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTE0LjkgMTcuNDVDMTYuMjUgMTcuNDUgMTcuMzUgMTYuMzUgMTcuMzUgMTVDMTcuMzUgMTMuNjUgMTYuMjUgMTIuNTUgMTQuOSAxMi41NUMxMy41NCAxMi41NSAxMi40NSAxMy42NSAxMi40NSAxNUMxMi40NSAxNi4zNSAxMy41NCAxNy40NSAxNC45IDE3LjQ1Wk0yMC4xIDE1LjY4TDIxLjU4IDE2Ljg0QzIxLjcxIDE2Ljk1IDIxLjc1IDE3LjEzIDIxLjY2IDE3LjI5TDIwLjI2IDE5LjcxQzIwLjE3IDE5Ljg2IDIwIDE5LjkyIDE5LjgzIDE5Ljg2TDE4LjA5IDE5LjE2QzE3LjczIDE5LjQ0IDE3LjMzIDE5LjY3IDE2LjkxIDE5Ljg1TDE2LjY0IDIxLjdDMTYuNjIgMjEuODcgMTYuNDcgMjIgMTYuMyAyMkgxMy41QzEzLjMyIDIyIDEzLjE4IDIxLjg3IDEzLjE1IDIxLjdMMTIuODkgMTkuODVDMTIuNDYgMTkuNjcgMTIuMDcgMTkuNDQgMTEuNzEgMTkuMTZMOS45NjAwMiAxOS44NkM5LjgxMDAyIDE5LjkyIDkuNjIwMDIgMTkuODYgOS41NDAwMiAxOS43MUw4LjE0MDAyIDE3LjI5QzguMDUwMDIgMTcuMTMgOC4wOTAwMiAxNi45NSA4LjIyMDAyIDE2Ljg0TDkuNzAwMDIgMTUuNjhMOS42NTAwMSAxNUw5LjcwMDAyIDE0LjMxTDguMjIwMDIgMTMuMTZDOC4wOTAwMiAxMy4wNSA4LjA1MDAyIDEyLjg2IDguMTQwMDIgMTIuNzFMOS41NDAwMiAxMC4yOUM5LjYyMDAyIDEwLjEzIDkuODEwMDIgMTAuMDcgOS45NjAwMiAxMC4xM0wxMS43MSAxMC44NEMxMi4wNyAxMC41NiAxMi40NiAxMC4zMiAxMi44OSAxMC4xNUwxMy4xNSA4LjI4OTk4QzEzLjE4IDguMTI5OTggMTMuMzIgNy45OTk5OCAxMy41IDcuOTk5OThIMTYuM0MxNi40NyA3Ljk5OTk4IDE2LjYyIDguMTI5OTggMTYuNjQgOC4yODk5OEwxNi45MSAxMC4xNUMxNy4zMyAxMC4zMiAxNy43MyAxMC41NiAxOC4wOSAxMC44NEwxOS44MyAxMC4xM0MyMCAxMC4wNyAyMC4xNyAxMC4xMyAyMC4yNiAxMC4yOUwyMS42NiAxMi43MUMyMS43NSAxMi44NiAyMS43MSAxMy4wNSAyMS41OCAxMy4xNkwyMC4xIDE0LjMxTDIwLjE1IDE1TDIwLjEgMTUuNjhaIi8+CiAgICA8cGF0aCBkPSJNNy4zMjk2NiA3LjQ0NDU0QzguMDgzMSA3LjAwOTU0IDguMzM5MzIgNi4wNTMzMiA3LjkwNDMyIDUuMjk5ODhDNy40NjkzMiA0LjU0NjQzIDYuNTA4MSA0LjI4MTU2IDUuNzU0NjYgNC43MTY1NkM1LjM5MTc2IDQuOTI2MDggNS4xMjY5NSA1LjI3MTE4IDUuMDE4NDkgNS42NzU5NEM0LjkxMDA0IDYuMDgwNzEgNC45NjY4MiA2LjUxMTk4IDUuMTc2MzQgNi44NzQ4OEM1LjYxMTM0IDcuNjI4MzIgNi41NzYyMiA3Ljg3OTU0IDcuMzI5NjYgNy40NDQ1NFpNOS42NTcxOCA0Ljc5NTkzTDEwLjg2NzIgNC45NTE3OUMxMC45NjI4IDQuOTc3NDEgMTEuMDQwMiA1LjA3MTMzIDExLjAzODIgNS4xODc5M0wxMS4wMzg4IDYuOTg4OTNDMTEuMDQ1NSA3LjEwMDU0IDEwLjk2MTYgNy4xOTUxOCAxMC44NTUgNy4yMTA1NEw5LjY2MDAxIDcuMzgwODNMOS4yMzkxNSA4LjEzMTg4TDkuNjY5NjEgOS4yNTc0NUM5LjcwNzI5IDkuMzYyNzEgOS42NjkzNCA5LjQ3Njk5IDkuNTc0MDggOS41MzE5OUw4LjAxNTIzIDEwLjQzMkM3LjkxMTMxIDEwLjQ5MiA3Ljc5MzM3IDEwLjQ2NzcgNy43MjEwNSAxMC4zODI0TDYuOTg3NDggOS40MzE4OEw2LjEwOTMxIDkuNDMwODNMNS4zNDcwNCAxMC4zOTA1QzUuMjg5MDkgMTAuNDcwMiA1LjE3MzgzIDEwLjQ5MDUgNS4wNzE4NyAxMC40MzM5TDMuNTEyNDUgOS41MzI5M0MzLjQxMDQ5IDkuNDc2MzMgMy4zNzY0NyA5LjM1NzQxIDMuNDEwNzUgOS4yNTY3OUwzLjg2MzQ3IDguMTQwOTNMMy42MTc0OSA3Ljc3NDg4TDMuNDIzNDcgNy4zNzg4M0wyLjIzMDc1IDcuMjEyOTdDMi4xMjY0NyA3LjE5MjM1IDIuMDQwNDkgNy4xMDM0MiAyLjA0MjQ1IDYuOTg2ODJMMi4wNDE4NyA1LjE4NTgyQzIuMDQzODMgNS4wNjkyMiAyLjExOTA5IDQuOTc5NTggMi4yMTcwNCA0Ljk2OTIyTDMuNDIwNjUgNC43OTM5M0wzLjg2NzQ5IDQuMDI3ODhMMy40MTEwNSAyLjkxNzMxQzMuMzczMzcgMi44MTIwNCAzLjQxMTMxIDIuNjk3NzYgMy41MTUyMyAyLjYzNzc2TDUuMDc0MDggMS43Mzc3NkM1LjE2OTM0IDEuNjgyNzYgNS4yODcyOSAxLjcwNzA0IDUuMzU5NjEgMS43OTIzMUw2LjExOTE1IDIuNzI3ODhMNi45ODAwMSAyLjczODkzTDcuNzI0OTYgMS43ODkyMkM3Ljc5MTU2IDEuNzA0NTggNy45MTU0OCAxLjY3OTIyIDguMDA4NzkgMS43NDA4Mkw5LjU2ODIxIDIuNjQxODJDOS42NzAxNyAyLjY5ODQyIDkuNzEyODUgMi44MTIzNCA5LjY4NzIzIDIuOTA3OTdMOS4yMTcxOCA0LjAzMzgzTDkuNDYzMTYgNC4zOTk4OEw5LjY1NzE4IDQuNzk1OTNaIi8+CiAgPC9nPgo8L3N2Zz4K);
    --jp-icon-caret-down-empty-thin: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwIDIwIj4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSIgc2hhcGUtcmVuZGVyaW5nPSJnZW9tZXRyaWNQcmVjaXNpb24iPgoJCTxwb2x5Z29uIGNsYXNzPSJzdDEiIHBvaW50cz0iOS45LDEzLjYgMy42LDcuNCA0LjQsNi42IDkuOSwxMi4yIDE1LjQsNi43IDE2LjEsNy40ICIvPgoJPC9nPgo8L3N2Zz4K);
    --jp-icon-caret-down-empty: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiIHNoYXBlLXJlbmRlcmluZz0iZ2VvbWV0cmljUHJlY2lzaW9uIj4KICAgIDxwYXRoIGQ9Ik01LjIsNS45TDksOS43bDMuOC0zLjhsMS4yLDEuMmwtNC45LDVsLTQuOS01TDUuMiw1Ljl6Ii8+CiAgPC9nPgo8L3N2Zz4K);
    --jp-icon-caret-down: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiIHNoYXBlLXJlbmRlcmluZz0iZ2VvbWV0cmljUHJlY2lzaW9uIj4KICAgIDxwYXRoIGQ9Ik01LjIsNy41TDksMTEuMmwzLjgtMy44SDUuMnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
    --jp-icon-caret-left: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSIgc2hhcGUtcmVuZGVyaW5nPSJnZW9tZXRyaWNQcmVjaXNpb24iPgoJCTxwYXRoIGQ9Ik0xMC44LDEyLjhMNy4xLDlsMy44LTMuOGwwLDcuNkgxMC44eiIvPgogIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-caret-right: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiIHNoYXBlLXJlbmRlcmluZz0iZ2VvbWV0cmljUHJlY2lzaW9uIj4KICAgIDxwYXRoIGQ9Ik03LjIsNS4yTDEwLjksOWwtMy44LDMuOFY1LjJINy4yeiIvPgogIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-caret-up-empty-thin: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwIDIwIj4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSIgc2hhcGUtcmVuZGVyaW5nPSJnZW9tZXRyaWNQcmVjaXNpb24iPgoJCTxwb2x5Z29uIGNsYXNzPSJzdDEiIHBvaW50cz0iMTUuNCwxMy4zIDkuOSw3LjcgNC40LDEzLjIgMy42LDEyLjUgOS45LDYuMyAxNi4xLDEyLjYgIi8+Cgk8L2c+Cjwvc3ZnPgo=);
    --jp-icon-caret-up: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSIgc2hhcGUtcmVuZGVyaW5nPSJnZW9tZXRyaWNQcmVjaXNpb24iPgoJCTxwYXRoIGQ9Ik01LjIsMTAuNUw5LDYuOGwzLjgsMy44SDUuMnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
    --jp-icon-case-sensitive: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwIDIwIj4KICA8ZyBjbGFzcz0ianAtaWNvbjIiIGZpbGw9IiM0MTQxNDEiPgogICAgPHJlY3QgeD0iMiIgeT0iMiIgd2lkdGg9IjE2IiBoZWlnaHQ9IjE2Ii8+CiAgPC9nPgogIDxnIGNsYXNzPSJqcC1pY29uLWFjY2VudDIiIGZpbGw9IiNGRkYiPgogICAgPHBhdGggZD0iTTcuNiw4aDAuOWwzLjUsOGgtMS4xTDEwLDE0SDZsLTAuOSwySDRMNy42LDh6IE04LDkuMUw2LjQsMTNoMy4yTDgsOS4xeiIvPgogICAgPHBhdGggZD0iTTE2LjYsOS44Yy0wLjIsMC4xLTAuNCwwLjEtMC43LDAuMWMtMC4yLDAtMC40LTAuMS0wLjYtMC4yYy0wLjEtMC4xLTAuMi0wLjQtMC4yLTAuNyBjLTAuMywwLjMtMC42LDAuNS0wLjksMC43Yy0wLjMsMC4xLTAuNywwLjItMS4xLDAuMmMtMC4zLDAtMC41LDAtMC43LTAuMWMtMC4yLTAuMS0wLjQtMC4yLTAuNi0wLjNjLTAuMi0wLjEtMC4zLTAuMy0wLjQtMC41IGMtMC4xLTAuMi0wLjEtMC40LTAuMS0wLjdjMC0wLjMsMC4xLTAuNiwwLjItMC44YzAuMS0wLjIsMC4zLTAuNCwwLjQtMC41QzEyLDcsMTIuMiw2LjksMTIuNSw2LjhjMC4yLTAuMSwwLjUtMC4xLDAuNy0wLjIgYzAuMy0wLjEsMC41LTAuMSwwLjctMC4xYzAuMiwwLDAuNC0wLjEsMC42LTAuMWMwLjIsMCwwLjMtMC4xLDAuNC0wLjJjMC4xLTAuMSwwLjItMC4yLDAuMi0wLjRjMC0xLTEuMS0xLTEuMy0xIGMtMC40LDAtMS40LDAtMS40LDEuMmgtMC45YzAtMC40LDAuMS0wLjcsMC4yLTFjMC4xLTAuMiwwLjMtMC40LDAuNS0wLjZjMC4yLTAuMiwwLjUtMC4zLDAuOC0wLjNDMTMuMyw0LDEzLjYsNCwxMy45LDQgYzAuMywwLDAuNSwwLDAuOCwwLjFjMC4zLDAsMC41LDAuMSwwLjcsMC4yYzAuMiwwLjEsMC40LDAuMywwLjUsMC41QzE2LDUsMTYsNS4yLDE2LDUuNnYyLjljMCwwLjIsMCwwLjQsMCwwLjUgYzAsMC4xLDAuMSwwLjIsMC4zLDAuMmMwLjEsMCwwLjIsMCwwLjMsMFY5Ljh6IE0xNS4yLDYuOWMtMS4yLDAuNi0zLjEsMC4yLTMuMSwxLjRjMCwxLjQsMy4xLDEsMy4xLTAuNVY2Ljl6Ii8+CiAgPC9nPgo8L3N2Zz4K);
    --jp-icon-check: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTkgMTYuMTdMNC44MyAxMmwtMS40MiAxLjQxTDkgMTkgMjEgN2wtMS40MS0xLjQxeiIvPgogIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-circle-empty: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEyIDJDNi40NyAyIDIgNi40NyAyIDEyczQuNDcgMTAgMTAgMTAgMTAtNC40NyAxMC0xMFMxNy41MyAyIDEyIDJ6bTAgMThjLTQuNDEgMC04LTMuNTktOC04czMuNTktOCA4LTggOCAzLjU5IDggOC0zLjU5IDgtOCA4eiIvPgogIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-circle: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMTggMTgiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPGNpcmNsZSBjeD0iOSIgY3k9IjkiIHI9IjgiLz4KICA8L2c+Cjwvc3ZnPgo=);
    --jp-icon-clear: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8bWFzayBpZD0iZG9udXRIb2xlIj4KICAgIDxyZWN0IHdpZHRoPSIyNCIgaGVpZ2h0PSIyNCIgZmlsbD0id2hpdGUiIC8+CiAgICA8Y2lyY2xlIGN4PSIxMiIgY3k9IjEyIiByPSI4IiBmaWxsPSJibGFjayIvPgogIDwvbWFzaz4KCiAgPGcgY2xhc3M9ImpwLWljb24zIiBmaWxsPSIjNjE2MTYxIj4KICAgIDxyZWN0IGhlaWdodD0iMTgiIHdpZHRoPSIyIiB4PSIxMSIgeT0iMyIgdHJhbnNmb3JtPSJyb3RhdGUoMzE1LCAxMiwgMTIpIi8+CiAgICA8Y2lyY2xlIGN4PSIxMiIgY3k9IjEyIiByPSIxMCIgbWFzaz0idXJsKCNkb251dEhvbGUpIi8+CiAgPC9nPgo8L3N2Zz4K);
    --jp-icon-close: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbi1ub25lIGpwLWljb24tc2VsZWN0YWJsZS1pbnZlcnNlIGpwLWljb24zLWhvdmVyIiBmaWxsPSJub25lIj4KICAgIDxjaXJjbGUgY3g9IjEyIiBjeT0iMTIiIHI9IjExIi8+CiAgPC9nPgoKICA8ZyBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIGpwLWljb24tYWNjZW50Mi1ob3ZlciIgZmlsbD0iIzYxNjE2MSI+CiAgICA8cGF0aCBkPSJNMTkgNi40MUwxNy41OSA1IDEyIDEwLjU5IDYuNDEgNSA1IDYuNDEgMTAuNTkgMTIgNSAxNy41OSA2LjQxIDE5IDEyIDEzLjQxIDE3LjU5IDE5IDE5IDE3LjU5IDEzLjQxIDEyeiIvPgogIDwvZz4KCiAgPGcgY2xhc3M9ImpwLWljb24tbm9uZSBqcC1pY29uLWJ1c3kiIGZpbGw9Im5vbmUiPgogICAgPGNpcmNsZSBjeD0iMTIiIGN5PSIxMiIgcj0iNyIvPgogIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-code: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjIiIGhlaWdodD0iMjIiIHZpZXdCb3g9IjAgMCAyOCAyOCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CgkJPHBhdGggZD0iTTExLjQgMTguNkw2LjggMTRMMTEuNCA5LjRMMTAgOEw0IDE0TDEwIDIwTDExLjQgMTguNlpNMTYuNiAxOC42TDIxLjIgMTRMMTYuNiA5LjRMMTggOEwyNCAxNEwxOCAyMEwxNi42IDE4LjZWMTguNloiLz4KCTwvZz4KPC9zdmc+Cg==);
    --jp-icon-console: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwMCAyMDAiPgogIDxnIGNsYXNzPSJqcC1pY29uLWJyYW5kMSBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiMwMjg4RDEiPgogICAgPHBhdGggZD0iTTIwIDE5LjhoMTYwdjE1OS45SDIweiIvPgogIDwvZz4KICA8ZyBjbGFzcz0ianAtaWNvbi1zZWxlY3RhYmxlLWludmVyc2UiIGZpbGw9IiNmZmYiPgogICAgPHBhdGggZD0iTTEwNSAxMjcuM2g0MHYxMi44aC00MHpNNTEuMSA3N0w3NCA5OS45bC0yMy4zIDIzLjMgMTAuNSAxMC41IDIzLjMtMjMuM0w5NSA5OS45IDg0LjUgODkuNCA2MS42IDY2LjV6Ii8+CiAgPC9nPgo8L3N2Zz4K);
    --jp-icon-copy: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMTggMTgiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTExLjksMUgzLjJDMi40LDEsMS43LDEuNywxLjcsMi41djEwLjJoMS41VjIuNWg4LjdWMXogTTE0LjEsMy45aC04Yy0wLjgsMC0xLjUsMC43LTEuNSwxLjV2MTAuMmMwLDAuOCwwLjcsMS41LDEuNSwxLjVoOCBjMC44LDAsMS41LTAuNywxLjUtMS41VjUuNEMxNS41LDQuNiwxNC45LDMuOSwxNC4xLDMuOXogTTE0LjEsMTUuNWgtOFY1LjRoOFYxNS41eiIvPgogIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-cut: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTkuNjQgNy42NGMuMjMtLjUuMzYtMS4wNS4zNi0xLjY0IDAtMi4yMS0xLjc5LTQtNC00UzIgMy43OSAyIDZzMS43OSA0IDQgNGMuNTkgMCAxLjE0LS4xMyAxLjY0LS4zNkwxMCAxMmwtMi4zNiAyLjM2QzcuMTQgMTQuMTMgNi41OSAxNCA2IDE0Yy0yLjIxIDAtNCAxLjc5LTQgNHMxLjc5IDQgNCA0IDQtMS43OSA0LTRjMC0uNTktLjEzLTEuMTQtLjM2LTEuNjRMMTIgMTRsNyA3aDN2LTFMOS42NCA3LjY0ek02IDhjLTEuMSAwLTItLjg5LTItMnMuOS0yIDItMiAyIC44OSAyIDItLjkgMi0yIDJ6bTAgMTJjLTEuMSAwLTItLjg5LTItMnMuOS0yIDItMiAyIC44OSAyIDItLjkgMi0yIDJ6bTYtNy41Yy0uMjggMC0uNS0uMjItLjUtLjVzLjIyLS41LjUtLjUuNS4yMi41LjUtLjIyLjUtLjUuNXpNMTkgM2wtNiA2IDIgMiA3LTdWM3oiLz4KICA8L2c+Cjwvc3ZnPgo=);
    --jp-icon-download: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTE5IDloLTRWM0g5djZINWw3IDcgNy03ek01IDE4djJoMTR2LTJINXoiLz4KICA8L2c+Cjwvc3ZnPgo=);
    --jp-icon-edit: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTMgMTcuMjVWMjFoMy43NUwxNy44MSA5Ljk0bC0zLjc1LTMuNzVMMyAxNy4yNXpNMjAuNzEgNy4wNGMuMzktLjM5LjM5LTEuMDIgMC0xLjQxbC0yLjM0LTIuMzRjLS4zOS0uMzktMS4wMi0uMzktMS40MSAwbC0xLjgzIDEuODMgMy43NSAzLjc1IDEuODMtMS44M3oiLz4KICA8L2c+Cjwvc3ZnPgo=);
    --jp-icon-ellipses: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPGNpcmNsZSBjeD0iNSIgY3k9IjEyIiByPSIyIi8+CiAgICA8Y2lyY2xlIGN4PSIxMiIgY3k9IjEyIiByPSIyIi8+CiAgICA8Y2lyY2xlIGN4PSIxOSIgY3k9IjEyIiByPSIyIi8+CiAgPC9nPgo8L3N2Zz4K);
    --jp-icon-extension: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTIwLjUgMTFIMTlWN2MwLTEuMS0uOS0yLTItMmgtNFYzLjVDMTMgMi4xMiAxMS44OCAxIDEwLjUgMVM4IDIuMTIgOCAzLjVWNUg0Yy0xLjEgMC0xLjk5LjktMS45OSAydjMuOEgzLjVjMS40OSAwIDIuNyAxLjIxIDIuNyAyLjdzLTEuMjEgMi43LTIuNyAyLjdIMlYyMGMwIDEuMS45IDIgMiAyaDMuOHYtMS41YzAtMS40OSAxLjIxLTIuNyAyLjctMi43IDEuNDkgMCAyLjcgMS4yMSAyLjcgMi43VjIySDE3YzEuMSAwIDItLjkgMi0ydi00aDEuNWMxLjM4IDAgMi41LTEuMTIgMi41LTIuNVMyMS44OCAxMSAyMC41IDExeiIvPgogIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-fast-forward: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyNCIgaGVpZ2h0PSIyNCIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTQgMThsOC41LTZMNCA2djEyem05LTEydjEybDguNS02TDEzIDZ6Ii8+CiAgICA8L2c+Cjwvc3ZnPgo=);
    --jp-icon-file-upload: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTkgMTZoNnYtNmg0bC03LTctNyA3aDR6bS00IDJoMTR2Mkg1eiIvPgogIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-file: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMTkuMyA4LjJsLTUuNS01LjVjLS4zLS4zLS43LS41LTEuMi0uNUgzLjljLS44LjEtMS42LjktMS42IDEuOHYxNC4xYzAgLjkuNyAxLjYgMS42IDEuNmgxNC4yYy45IDAgMS42LS43IDEuNi0xLjZWOS40Yy4xLS41LS4xLS45LS40LTEuMnptLTUuOC0zLjNsMy40IDMuNmgtMy40VjQuOXptMy45IDEyLjdINC43Yy0uMSAwLS4yIDAtLjItLjJWNC43YzAtLjIuMS0uMy4yLS4zaDcuMnY0LjRzMCAuOC4zIDEuMWMuMy4zIDEuMS4zIDEuMS4zaDQuM3Y3LjJzLS4xLjItLjIuMnoiLz4KPC9zdmc+Cg==);
    --jp-icon-filter-list: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEwIDE4aDR2LTJoLTR2MnpNMyA2djJoMThWNkgzem0zIDdoMTJ2LTJINnYyeiIvPgogIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-folder: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMTAgNEg0Yy0xLjEgMC0xLjk5LjktMS45OSAyTDIgMThjMCAxLjEuOSAyIDIgMmgxNmMxLjEgMCAyLS45IDItMlY4YzAtMS4xLS45LTItMi0yaC04bC0yLTJ6Ii8+Cjwvc3ZnPgo=);
    --jp-icon-html5: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDUxMiA1MTIiPgogIDxwYXRoIGNsYXNzPSJqcC1pY29uMCBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiMwMDAiIGQ9Ik0xMDguNCAwaDIzdjIyLjhoMjEuMlYwaDIzdjY5aC0yM1Y0NmgtMjF2MjNoLTIzLjJNMjA2IDIzaC0yMC4zVjBoNjMuN3YyM0gyMjl2NDZoLTIzbTUzLjUtNjloMjQuMWwxNC44IDI0LjNMMzEzLjIgMGgyNC4xdjY5aC0yM1YzNC44bC0xNi4xIDI0LjgtMTYuMS0yNC44VjY5aC0yMi42bTg5LjItNjloMjN2NDYuMmgzMi42VjY5aC01NS42Ii8+CiAgPHBhdGggY2xhc3M9ImpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iI2U0NGQyNiIgZD0iTTEwNy42IDQ3MWwtMzMtMzcwLjRoMzYyLjhsLTMzIDM3MC4yTDI1NS43IDUxMiIvPgogIDxwYXRoIGNsYXNzPSJqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiNmMTY1MjkiIGQ9Ik0yNTYgNDgwLjVWMTMxaDE0OC4zTDM3NiA0NDciLz4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1zZWxlY3RhYmxlLWludmVyc2UiIGZpbGw9IiNlYmViZWIiIGQ9Ik0xNDIgMTc2LjNoMTE0djQ1LjRoLTY0LjJsNC4yIDQ2LjVoNjB2NDUuM0gxNTQuNG0yIDIyLjhIMjAybDMuMiAzNi4zIDUwLjggMTMuNnY0Ny40bC05My4yLTI2Ii8+CiAgPHBhdGggY2xhc3M9ImpwLWljb24tc2VsZWN0YWJsZS1pbnZlcnNlIiBmaWxsPSIjZmZmIiBkPSJNMzY5LjYgMTc2LjNIMjU1Ljh2NDUuNGgxMDkuNm0tNC4xIDQ2LjVIMjU1Ljh2NDUuNGg1NmwtNS4zIDU5LTUwLjcgMTMuNnY0Ny4ybDkzLTI1LjgiLz4KPC9zdmc+Cg==);
    --jp-icon-image: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1icmFuZDQganAtaWNvbi1zZWxlY3RhYmxlLWludmVyc2UiIGZpbGw9IiNGRkYiIGQ9Ik0yLjIgMi4yaDE3LjV2MTcuNUgyLjJ6Ii8+CiAgPHBhdGggY2xhc3M9ImpwLWljb24tYnJhbmQwIGpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iIzNGNTFCNSIgZD0iTTIuMiAyLjJ2MTcuNWgxNy41bC4xLTE3LjVIMi4yem0xMi4xIDIuMmMxLjIgMCAyLjIgMSAyLjIgMi4ycy0xIDIuMi0yLjIgMi4yLTIuMi0xLTIuMi0yLjIgMS0yLjIgMi4yLTIuMnpNNC40IDE3LjZsMy4zLTguOCAzLjMgNi42IDIuMi0zLjIgNC40IDUuNEg0LjR6Ii8+Cjwvc3ZnPgo=);
    --jp-icon-inspector: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMjAgNEg0Yy0xLjEgMC0xLjk5LjktMS45OSAyTDIgMThjMCAxLjEuOSAyIDIgMmgxNmMxLjEgMCAyLS45IDItMlY2YzAtMS4xLS45LTItMi0yem0tNSAxNEg0di00aDExdjR6bTAtNUg0VjloMTF2NHptNSA1aC00VjloNHY5eiIvPgo8L3N2Zz4K);
    --jp-icon-json: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8ZyBjbGFzcz0ianAtaWNvbi13YXJuMSBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiNGOUE4MjUiPgogICAgPHBhdGggZD0iTTIwLjIgMTEuOGMtMS42IDAtMS43LjUtMS43IDEgMCAuNC4xLjkuMSAxLjMuMS41LjEuOS4xIDEuMyAwIDEuNy0xLjQgMi4zLTMuNSAyLjNoLS45di0xLjloLjVjMS4xIDAgMS40IDAgMS40LS44IDAtLjMgMC0uNi0uMS0xIDAtLjQtLjEtLjgtLjEtMS4yIDAtMS4zIDAtMS44IDEuMy0yLTEuMy0uMi0xLjMtLjctMS4zLTIgMC0uNC4xLS44LjEtMS4yLjEtLjQuMS0uNy4xLTEgMC0uOC0uNC0uNy0xLjQtLjhoLS41VjQuMWguOWMyLjIgMCAzLjUuNyAzLjUgMi4zIDAgLjQtLjEuOS0uMSAxLjMtLjEuNS0uMS45LS4xIDEuMyAwIC41LjIgMSAxLjcgMXYxLjh6TTEuOCAxMC4xYzEuNiAwIDEuNy0uNSAxLjctMSAwLS40LS4xLS45LS4xLTEuMy0uMS0uNS0uMS0uOS0uMS0xLjMgMC0xLjYgMS40LTIuMyAzLjUtMi4zaC45djEuOWgtLjVjLTEgMC0xLjQgMC0xLjQuOCAwIC4zIDAgLjYuMSAxIDAgLjIuMS42LjEgMSAwIDEuMyAwIDEuOC0xLjMgMkM2IDExLjIgNiAxMS43IDYgMTNjMCAuNC0uMS44LS4xIDEuMi0uMS4zLS4xLjctLjEgMSAwIC44LjMuOCAxLjQuOGguNXYxLjloLS45Yy0yLjEgMC0zLjUtLjYtMy41LTIuMyAwLS40LjEtLjkuMS0xLjMuMS0uNS4xLS45LjEtMS4zIDAtLjUtLjItMS0xLjctMXYtMS45eiIvPgogICAgPGNpcmNsZSBjeD0iMTEiIGN5PSIxMy44IiByPSIyLjEiLz4KICAgIDxjaXJjbGUgY3g9IjExIiBjeT0iOC4yIiByPSIyLjEiLz4KICA8L2c+Cjwvc3ZnPgo=);
    --jp-icon-jupyter-favicon: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTUyIiBoZWlnaHQ9IjE2NSIgdmlld0JveD0iMCAwIDE1MiAxNjUiIHZlcnNpb249IjEuMSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbi13YXJuMCIgZmlsbD0iI0YzNzcyNiI+CiAgICA8cGF0aCB0cmFuc2Zvcm09InRyYW5zbGF0ZSgwLjA3ODk0NywgMTEwLjU4MjkyNykiIGQ9Ik03NS45NDIyODQyLDI5LjU4MDQ1NjEgQzQzLjMwMjM5NDcsMjkuNTgwNDU2MSAxNC43OTY3ODMyLDE3LjY1MzQ2MzQgMCwwIEM1LjUxMDgzMjExLDE1Ljg0MDY4MjkgMTUuNzgxNTM4OSwyOS41NjY3NzMyIDI5LjM5MDQ5NDcsMzkuMjc4NDE3MSBDNDIuOTk5Nyw0OC45ODk4NTM3IDU5LjI3MzcsNTQuMjA2NzgwNSA3NS45NjA1Nzg5LDU0LjIwNjc4MDUgQzkyLjY0NzQ1NzksNTQuMjA2NzgwNSAxMDguOTIxNDU4LDQ4Ljk4OTg1MzcgMTIyLjUzMDY2MywzOS4yNzg0MTcxIEMxMzYuMTM5NDUzLDI5LjU2Njc3MzIgMTQ2LjQxMDI4NCwxNS44NDA2ODI5IDE1MS45MjExNTgsMCBDMTM3LjA4Nzg2OCwxNy42NTM0NjM0IDEwOC41ODI1ODksMjkuNTgwNDU2MSA3NS45NDIyODQyLDI5LjU4MDQ1NjEgTDc1Ljk0MjI4NDIsMjkuNTgwNDU2MSBaIiAvPgogICAgPHBhdGggdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMC4wMzczNjgsIDAuNzA0ODc4KSIgZD0iTTc1Ljk3ODQ1NzksMjQuNjI2NDA3MyBDMTA4LjYxODc2MywyNC42MjY0MDczIDEzNy4xMjQ0NTgsMzYuNTUzNDQxNSAxNTEuOTIxMTU4LDU0LjIwNjc4MDUgQzE0Ni40MTAyODQsMzguMzY2MjIyIDEzNi4xMzk0NTMsMjQuNjQwMTMxNyAxMjIuNTMwNjYzLDE0LjkyODQ4NzggQzEwOC45MjE0NTgsNS4yMTY4NDM5IDkyLjY0NzQ1NzksMCA3NS45NjA1Nzg5LDAgQzU5LjI3MzcsMCA0Mi45OTk3LDUuMjE2ODQzOSAyOS4zOTA0OTQ3LDE0LjkyODQ4NzggQzE1Ljc4MTUzODksMjQuNjQwMTMxNyA1LjUxMDgzMjExLDM4LjM2NjIyMiAwLDU0LjIwNjc4MDUgQzE0LjgzMzA4MTYsMzYuNTg5OTI5MyA0My4zMzg1Njg0LDI0LjYyNjQwNzMgNzUuOTc4NDU3OSwyNC42MjY0MDczIEw3NS45Nzg0NTc5LDI0LjYyNjQwNzMgWiIgLz4KICA8L2c+Cjwvc3ZnPgo=);
    --jp-icon-jupyter: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMzkiIGhlaWdodD0iNTEiIHZpZXdCb3g9IjAgMCAzOSA1MSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSgtMTYzOCAtMjI4MSkiPgogICAgPGcgY2xhc3M9ImpwLWljb24td2FybjAiIGZpbGw9IiNGMzc3MjYiPgogICAgICA8cGF0aCB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxNjM5Ljc0IDIzMTEuOTgpIiBkPSJNIDE4LjI2NDYgNy4xMzQxMUMgMTAuNDE0NSA3LjEzNDExIDMuNTU4NzIgNC4yNTc2IDAgMEMgMS4zMjUzOSAzLjgyMDQgMy43OTU1NiA3LjEzMDgxIDcuMDY4NiA5LjQ3MzAzQyAxMC4zNDE3IDExLjgxNTIgMTQuMjU1NyAxMy4wNzM0IDE4LjI2OSAxMy4wNzM0QyAyMi4yODIzIDEzLjA3MzQgMjYuMTk2MyAxMS44MTUyIDI5LjQ2OTQgOS40NzMwM0MgMzIuNzQyNCA3LjEzMDgxIDM1LjIxMjYgMy44MjA0IDM2LjUzOCAwQyAzMi45NzA1IDQuMjU3NiAyNi4xMTQ4IDcuMTM0MTEgMTguMjY0NiA3LjEzNDExWiIvPgogICAgICA8cGF0aCB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxNjM5LjczIDIyODUuNDgpIiBkPSJNIDE4LjI3MzMgNS45MzkzMUMgMjYuMTIzNSA1LjkzOTMxIDMyLjk3OTMgOC44MTU4MyAzNi41MzggMTMuMDczNEMgMzUuMjEyNiA5LjI1MzAzIDMyLjc0MjQgNS45NDI2MiAyOS40Njk0IDMuNjAwNEMgMjYuMTk2MyAxLjI1ODE4IDIyLjI4MjMgMCAxOC4yNjkgMEMgMTQuMjU1NyAwIDEwLjM0MTcgMS4yNTgxOCA3LjA2ODYgMy42MDA0QyAzLjc5NTU2IDUuOTQyNjIgMS4zMjUzOSA5LjI1MzAzIDAgMTMuMDczNEMgMy41Njc0NSA4LjgyNDYzIDEwLjQyMzIgNS45MzkzMSAxOC4yNzMzIDUuOTM5MzFaIi8+CiAgICA8L2c+CiAgICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgICA8cGF0aCB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxNjY5LjMgMjI4MS4zMSkiIGQ9Ik0gNS44OTM1MyAyLjg0NEMgNS45MTg4OSAzLjQzMTY1IDUuNzcwODUgNC4wMTM2NyA1LjQ2ODE1IDQuNTE2NDVDIDUuMTY1NDUgNS4wMTkyMiA0LjcyMTY4IDUuNDIwMTUgNC4xOTI5OSA1LjY2ODUxQyAzLjY2NDMgNS45MTY4OCAzLjA3NDQ0IDYuMDAxNTEgMi40OTgwNSA1LjkxMTcxQyAxLjkyMTY2IDUuODIxOSAxLjM4NDYzIDUuNTYxNyAwLjk1NDg5OCA1LjE2NDAxQyAwLjUyNTE3IDQuNzY2MzMgMC4yMjIwNTYgNC4yNDkwMyAwLjA4MzkwMzcgMy42Nzc1N0MgLTAuMDU0MjQ4MyAzLjEwNjExIC0wLjAyMTIzIDIuNTA2MTcgMC4xNzg3ODEgMS45NTM2NEMgMC4zNzg3OTMgMS40MDExIDAuNzM2ODA5IDAuOTIwODE3IDEuMjA3NTQgMC41NzM1MzhDIDEuNjc4MjYgMC4yMjYyNTkgMi4yNDA1NSAwLjAyNzU5MTkgMi44MjMyNiAwLjAwMjY3MjI5QyAzLjYwMzg5IC0wLjAzMDcxMTUgNC4zNjU3MyAwLjI0OTc4OSA0Ljk0MTQyIDAuNzgyNTUxQyA1LjUxNzExIDEuMzE1MzEgNS44NTk1NiAyLjA1Njc2IDUuODkzNTMgMi44NDRaIi8+CiAgICAgIDxwYXRoIHRyYW5zZm9ybT0idHJhbnNsYXRlKDE2MzkuOCAyMzIzLjgxKSIgZD0iTSA3LjQyNzg5IDMuNTgzMzhDIDcuNDYwMDggNC4zMjQzIDcuMjczNTUgNS4wNTgxOSA2Ljg5MTkzIDUuNjkyMTNDIDYuNTEwMzEgNi4zMjYwNyA1Ljk1MDc1IDYuODMxNTYgNS4yODQxMSA3LjE0NDZDIDQuNjE3NDcgNy40NTc2MyAzLjg3MzcxIDcuNTY0MTQgMy4xNDcwMiA3LjQ1MDYzQyAyLjQyMDMyIDcuMzM3MTIgMS43NDMzNiA3LjAwODcgMS4yMDE4NCA2LjUwNjk1QyAwLjY2MDMyOCA2LjAwNTIgMC4yNzg2MSA1LjM1MjY4IDAuMTA1MDE3IDQuNjMyMDJDIC0wLjA2ODU3NTcgMy45MTEzNSAtMC4wMjYyMzYxIDMuMTU0OTQgMC4yMjY2NzUgMi40NTg1NkMgMC40Nzk1ODcgMS43NjIxNyAwLjkzMTY5NyAxLjE1NzEzIDEuNTI1NzYgMC43MjAwMzNDIDIuMTE5ODMgMC4yODI5MzUgMi44MjkxNCAwLjAzMzQzOTUgMy41NjM4OSAwLjAwMzEzMzQ0QyA0LjU0NjY3IC0wLjAzNzQwMzMgNS41MDUyOSAwLjMxNjcwNiA2LjIyOTYxIDAuOTg3ODM1QyA2Ljk1MzkzIDEuNjU4OTYgNy4zODQ4NCAyLjU5MjM1IDcuNDI3ODkgMy41ODMzOEwgNy40Mjc4OSAzLjU4MzM4WiIvPgogICAgICA8cGF0aCB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxNjM4LjM2IDIyODYuMDYpIiBkPSJNIDIuMjc0NzEgNC4zOTYyOUMgMS44NDM2MyA0LjQxNTA4IDEuNDE2NzEgNC4zMDQ0NSAxLjA0Nzk5IDQuMDc4NDNDIDAuNjc5MjY4IDMuODUyNCAwLjM4NTMyOCAzLjUyMTE0IDAuMjAzMzcxIDMuMTI2NTZDIDAuMDIxNDEzNiAyLjczMTk4IC0wLjA0MDM3OTggMi4yOTE4MyAwLjAyNTgxMTYgMS44NjE4MUMgMC4wOTIwMDMxIDEuNDMxOCAwLjI4MzIwNCAxLjAzMTI2IDAuNTc1MjEzIDAuNzEwODgzQyAwLjg2NzIyMiAwLjM5MDUxIDEuMjQ2OTEgMC4xNjQ3MDggMS42NjYyMiAwLjA2MjA1OTJDIDIuMDg1NTMgLTAuMDQwNTg5NyAyLjUyNTYxIC0wLjAxNTQ3MTQgMi45MzA3NiAwLjEzNDIzNUMgMy4zMzU5MSAwLjI4Mzk0MSAzLjY4NzkyIDAuNTUxNTA1IDMuOTQyMjIgMC45MDMwNkMgNC4xOTY1MiAxLjI1NDYyIDQuMzQxNjkgMS42NzQzNiA0LjM1OTM1IDIuMTA5MTZDIDQuMzgyOTkgMi42OTEwNyA0LjE3Njc4IDMuMjU4NjkgMy43ODU5NyAzLjY4NzQ2QyAzLjM5NTE2IDQuMTE2MjQgMi44NTE2NiA0LjM3MTE2IDIuMjc0NzEgNC4zOTYyOUwgMi4yNzQ3MSA0LjM5NjI5WiIvPgogICAgPC9nPgogIDwvZz4+Cjwvc3ZnPgo=);
    --jp-icon-jupyterlab-wordmark: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyMDAiIHZpZXdCb3g9IjAgMCAxODYwLjggNDc1Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjIiIGZpbGw9IiM0RTRFNEUiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDQ4MC4xMzY0MDEsIDY0LjI3MTQ5MykiPgogICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMC4wMDAwMDAsIDU4Ljg3NTU2NikiPgogICAgICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSgwLjA4NzYwMywgMC4xNDAyOTQpIj4KICAgICAgICA8cGF0aCBkPSJNLTQyNi45LDE2OS44YzAsNDguNy0zLjcsNjQuNy0xMy42LDc2LjRjLTEwLjgsMTAtMjUsMTUuNS0zOS43LDE1LjVsMy43LDI5IGMyMi44LDAuMyw0NC44LTcuOSw2MS45LTIzLjFjMTcuOC0xOC41LDI0LTQ0LjEsMjQtODMuM1YwSC00Mjd2MTcwLjFMLTQyNi45LDE2OS44TC00MjYuOSwxNjkuOHoiLz4KICAgICAgPC9nPgogICAgPC9nPgogICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMTU1LjA0NTI5NiwgNTYuODM3MTA0KSI+CiAgICAgIDxnIHRyYW5zZm9ybT0idHJhbnNsYXRlKDEuNTYyNDUzLCAxLjc5OTg0MikiPgogICAgICAgIDxwYXRoIGQ9Ik0tMzEyLDE0OGMwLDIxLDAsMzkuNSwxLjcsNTUuNGgtMzEuOGwtMi4xLTMzLjNoLTAuOGMtNi43LDExLjYtMTYuNCwyMS4zLTI4LDI3LjkgYy0xMS42LDYuNi0yNC44LDEwLTM4LjIsOS44Yy0zMS40LDAtNjktMTcuNy02OS04OVYwaDM2LjR2MTEyLjdjMCwzOC43LDExLjYsNjQuNyw0NC42LDY0LjdjMTAuMy0wLjIsMjAuNC0zLjUsMjguOS05LjQgYzguNS01LjksMTUuMS0xNC4zLDE4LjktMjMuOWMyLjItNi4xLDMuMy0xMi41LDMuMy0xOC45VjAuMmgzNi40VjE0OEgtMzEyTC0zMTIsMTQ4eiIvPgogICAgICA8L2c+CiAgICA8L2c+CiAgICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSgzOTAuMDEzMzIyLCA1My40Nzk2MzgpIj4KICAgICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMS43MDY0NTgsIDAuMjMxNDI1KSI+CiAgICAgICAgPHBhdGggZD0iTS00NzguNiw3MS40YzAtMjYtMC44LTQ3LTEuNy02Ni43aDMyLjdsMS43LDM0LjhoMC44YzcuMS0xMi41LDE3LjUtMjIuOCwzMC4xLTI5LjcgYzEyLjUtNywyNi43LTEwLjMsNDEtOS44YzQ4LjMsMCw4NC43LDQxLjcsODQuNywxMDMuM2MwLDczLjEtNDMuNywxMDkuMi05MSwxMDkuMmMtMTIuMSwwLjUtMjQuMi0yLjItMzUtNy44IGMtMTAuOC01LjYtMTkuOS0xMy45LTI2LjYtMjQuMmgtMC44VjI5MWgtMzZ2LTIyMEwtNDc4LjYsNzEuNEwtNDc4LjYsNzEuNHogTS00NDIuNiwxMjUuNmMwLjEsNS4xLDAuNiwxMC4xLDEuNywxNS4xIGMzLDEyLjMsOS45LDIzLjMsMTkuOCwzMS4xYzkuOSw3LjgsMjIuMSwxMi4xLDM0LjcsMTIuMWMzOC41LDAsNjAuNy0zMS45LDYwLjctNzguNWMwLTQwLjctMjEuMS03NS42LTU5LjUtNzUuNiBjLTEyLjksMC40LTI1LjMsNS4xLTM1LjMsMTMuNGMtOS45LDguMy0xNi45LDE5LjctMTkuNiwzMi40Yy0xLjUsNC45LTIuMywxMC0yLjUsMTUuMVYxMjUuNkwtNDQyLjYsMTI1LjZMLTQ0Mi42LDEyNS42eiIvPgogICAgICA8L2c+CiAgICA8L2c+CiAgICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSg2MDYuNzQwNzI2LCA1Ni44MzcxMDQpIj4KICAgICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMC43NTEyMjYsIDEuOTg5Mjk5KSI+CiAgICAgICAgPHBhdGggZD0iTS00NDAuOCwwbDQzLjcsMTIwLjFjNC41LDEzLjQsOS41LDI5LjQsMTIuOCw0MS43aDAuOGMzLjctMTIuMiw3LjktMjcuNywxMi44LTQyLjQgbDM5LjctMTE5LjJoMzguNUwtMzQ2LjksMTQ1Yy0yNiw2OS43LTQzLjcsMTA1LjQtNjguNiwxMjcuMmMtMTIuNSwxMS43LTI3LjksMjAtNDQuNiwyMy45bC05LjEtMzEuMSBjMTEuNy0zLjksMjIuNS0xMC4xLDMxLjgtMTguMWMxMy4yLTExLjEsMjMuNy0yNS4yLDMwLjYtNDEuMmMxLjUtMi44LDIuNS01LjcsMi45LTguOGMtMC4zLTMuMy0xLjItNi42LTIuNS05LjdMLTQ4MC4yLDAuMSBoMzkuN0wtNDQwLjgsMEwtNDQwLjgsMHoiLz4KICAgICAgPC9nPgogICAgPC9nPgogICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoODIyLjc0ODEwNCwgMC4wMDAwMDApIj4KICAgICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMS40NjQwNTAsIDAuMzc4OTE0KSI+CiAgICAgICAgPHBhdGggZD0iTS00MTMuNywwdjU4LjNoNTJ2MjguMmgtNTJWMTk2YzAsMjUsNywzOS41LDI3LjMsMzkuNWM3LjEsMC4xLDE0LjItMC43LDIxLjEtMi41IGwxLjcsMjcuN2MtMTAuMywzLjctMjEuMyw1LjQtMzIuMiw1Yy03LjMsMC40LTE0LjYtMC43LTIxLjMtMy40Yy02LjgtMi43LTEyLjktNi44LTE3LjktMTIuMWMtMTAuMy0xMC45LTE0LjEtMjktMTQuMS01Mi45IFY4Ni41aC0zMVY1OC4zaDMxVjkuNkwtNDEzLjcsMEwtNDEzLjcsMHoiLz4KICAgICAgPC9nPgogICAgPC9nPgogICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoOTc0LjQzMzI4NiwgNTMuNDc5NjM4KSI+CiAgICAgIDxnIHRyYW5zZm9ybT0idHJhbnNsYXRlKDAuOTkwMDM0LCAwLjYxMDMzOSkiPgogICAgICAgIDxwYXRoIGQ9Ik0tNDQ1LjgsMTEzYzAuOCw1MCwzMi4yLDcwLjYsNjguNiw3MC42YzE5LDAuNiwzNy45LTMsNTUuMy0xMC41bDYuMiwyNi40IGMtMjAuOSw4LjktNDMuNSwxMy4xLTY2LjIsMTIuNmMtNjEuNSwwLTk4LjMtNDEuMi05OC4zLTEwMi41Qy00ODAuMiw0OC4yLTQ0NC43LDAtMzg2LjUsMGM2NS4yLDAsODIuNyw1OC4zLDgyLjcsOTUuNyBjLTAuMSw1LjgtMC41LDExLjUtMS4yLDE3LjJoLTE0MC42SC00NDUuOEwtNDQ1LjgsMTEzeiBNLTMzOS4yLDg2LjZjMC40LTIzLjUtOS41LTYwLjEtNTAuNC02MC4xIGMtMzYuOCwwLTUyLjgsMzQuNC01NS43LDYwLjFILTMzOS4yTC0zMzkuMiw4Ni42TC0zMzkuMiw4Ni42eiIvPgogICAgICA8L2c+CiAgICA8L2c+CiAgICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxMjAxLjk2MTA1OCwgNTMuNDc5NjM4KSI+CiAgICAgIDxnIHRyYW5zZm9ybT0idHJhbnNsYXRlKDEuMTc5NjQwLCAwLjcwNTA2OCkiPgogICAgICAgIDxwYXRoIGQ9Ik0tNDc4LjYsNjhjMC0yMy45LTAuNC00NC41LTEuNy02My40aDMxLjhsMS4yLDM5LjloMS43YzkuMS0yNy4zLDMxLTQ0LjUsNTUuMy00NC41IGMzLjUtMC4xLDcsMC40LDEwLjMsMS4ydjM0LjhjLTQuMS0wLjktOC4yLTEuMy0xMi40LTEuMmMtMjUuNiwwLTQzLjcsMTkuNy00OC43LDQ3LjRjLTEsNS43LTEuNiwxMS41LTEuNywxNy4ydjEwOC4zaC0zNlY2OCBMLTQ3OC42LDY4eiIvPgogICAgICA8L2c+CiAgICA8L2c+CiAgPC9nPgoKICA8ZyBjbGFzcz0ianAtaWNvbi13YXJuMCIgZmlsbD0iI0YzNzcyNiI+CiAgICA8cGF0aCBkPSJNMTM1Mi4zLDMyNi4yaDM3VjI4aC0zN1YzMjYuMnogTTE2MDQuOCwzMjYuMmMtMi41LTEzLjktMy40LTMxLjEtMy40LTQ4Ljd2LTc2IGMwLTQwLjctMTUuMS04My4xLTc3LjMtODMuMWMtMjUuNiwwLTUwLDcuMS02Ni44LDE4LjFsOC40LDI0LjRjMTQuMy05LjIsMzQtMTUuMSw1My0xNS4xYzQxLjYsMCw0Ni4yLDMwLjIsNDYuMiw0N3Y0LjIgYy03OC42LTAuNC0xMjIuMywyNi41LTEyMi4zLDc1LjZjMCwyOS40LDIxLDU4LjQsNjIuMiw1OC40YzI5LDAsNTAuOS0xNC4zLDYyLjItMzAuMmgxLjNsMi45LDI1LjZIMTYwNC44eiBNMTU2NS43LDI1Ny43IGMwLDMuOC0wLjgsOC0yLjEsMTEuOGMtNS45LDE3LjItMjIuNywzNC00OS4yLDM0Yy0xOC45LDAtMzQuOS0xMS4zLTM0LjktMzUuM2MwLTM5LjUsNDUuOC00Ni42LDg2LjItNDUuOFYyNTcuN3ogTTE2OTguNSwzMjYuMiBsMS43LTMzLjZoMS4zYzE1LjEsMjYuOSwzOC43LDM4LjIsNjguMSwzOC4yYzQ1LjQsMCw5MS4yLTM2LjEsOTEuMi0xMDguOGMwLjQtNjEuNy0zNS4zLTEwMy43LTg1LjctMTAzLjcgYy0zMi44LDAtNTYuMywxNC43LTY5LjMsMzcuNGgtMC44VjI4aC0zNi42djI0NS43YzAsMTguMS0wLjgsMzguNi0xLjcsNTIuNUgxNjk4LjV6IE0xNzA0LjgsMjA4LjJjMC01LjksMS4zLTEwLjksMi4xLTE1LjEgYzcuNi0yOC4xLDMxLjEtNDUuNCw1Ni4zLTQ1LjRjMzkuNSwwLDYwLjUsMzQuOSw2MC41LDc1LjZjMCw0Ni42LTIzLjEsNzguMS02MS44LDc4LjFjLTI2LjksMC00OC4zLTE3LjYtNTUuNS00My4zIGMtMC44LTQuMi0xLjctOC44LTEuNy0xMy40VjIwOC4yeiIvPgogIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-kernel: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uMiIgZmlsbD0iIzYxNjE2MSIgZD0iTTE1IDlIOXY2aDZWOXptLTIgNGgtMnYtMmgydjJ6bTgtMlY5aC0yVjdjMC0xLjEtLjktMi0yLTJoLTJWM2gtMnYyaC0yVjNIOXYySDdjLTEuMSAwLTIgLjktMiAydjJIM3YyaDJ2MkgzdjJoMnYyYzAgMS4xLjkgMiAyIDJoMnYyaDJ2LTJoMnYyaDJ2LTJoMmMxLjEgMCAyLS45IDItMnYtMmgydi0yaC0ydi0yaDJ6bS00IDZIN1Y3aDEwdjEweiIvPgo8L3N2Zz4K);
    --jp-icon-keyboard: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMjAgNUg0Yy0xLjEgMC0xLjk5LjktMS45OSAyTDIgMTdjMCAxLjEuOSAyIDIgMmgxNmMxLjEgMCAyLS45IDItMlY3YzAtMS4xLS45LTItMi0yem0tOSAzaDJ2MmgtMlY4em0wIDNoMnYyaC0ydi0yek04IDhoMnYySDhWOHptMCAzaDJ2Mkg4di0yem0tMSAySDV2LTJoMnYyem0wLTNINVY4aDJ2MnptOSA3SDh2LTJoOHYyem0wLTRoLTJ2LTJoMnYyem0wLTNoLTJWOGgydjJ6bTMgM2gtMnYtMmgydjJ6bTAtM2gtMlY4aDJ2MnoiLz4KPC9zdmc+Cg==);
    --jp-icon-launcher: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMTkgMTlINVY1aDdWM0g1YTIgMiAwIDAwLTIgMnYxNGEyIDIgMCAwMDIgMmgxNGMxLjEgMCAyLS45IDItMnYtN2gtMnY3ek0xNCAzdjJoMy41OWwtOS44MyA5LjgzIDEuNDEgMS40MUwxOSA2LjQxVjEwaDJWM2gtN3oiLz4KPC9zdmc+Cg==);
    --jp-icon-line-form: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICAgIDxwYXRoIGZpbGw9IndoaXRlIiBkPSJNNS44OCA0LjEyTDEzLjc2IDEybC03Ljg4IDcuODhMOCAyMmwxMC0xMEw4IDJ6Ii8+Cjwvc3ZnPgo=);
    --jp-icon-link: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTMuOSAxMmMwLTEuNzEgMS4zOS0zLjEgMy4xLTMuMWg0VjdIN2MtMi43NiAwLTUgMi4yNC01IDVzMi4yNCA1IDUgNWg0di0xLjlIN2MtMS43MSAwLTMuMS0xLjM5LTMuMS0zLjF6TTggMTNoOHYtMkg4djJ6bTktNmgtNHYxLjloNGMxLjcxIDAgMy4xIDEuMzkgMy4xIDMuMXMtMS4zOSAzLjEtMy4xIDMuMWgtNFYxN2g0YzIuNzYgMCA1LTIuMjQgNS01cy0yLjI0LTUtNS01eiIvPgogIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-list: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uMiBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiM2MTYxNjEiIGQ9Ik0xOSA1djE0SDVWNWgxNG0xLjEtMkgzLjljLS41IDAtLjkuNC0uOS45djE2LjJjMCAuNC40LjkuOS45aDE2LjJjLjQgMCAuOS0uNS45LS45VjMuOWMwLS41LS41LS45LS45LS45ek0xMSA3aDZ2MmgtNlY3em0wIDRoNnYyaC02di0yem0wIDRoNnYyaC02ek03IDdoMnYySDd6bTAgNGgydjJIN3ptMCA0aDJ2Mkg3eiIvPgo8L3N2Zz4=);
    --jp-icon-listings-info: url(data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iaXNvLTg4NTktMSI/Pg0KPHN2ZyB2ZXJzaW9uPSIxLjEiIGlkPSJDYXBhXzEiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgeG1sbnM6eGxpbms9Imh0dHA6Ly93d3cudzMub3JnLzE5OTkveGxpbmsiIHg9IjBweCIgeT0iMHB4Ig0KCSB2aWV3Qm94PSIwIDAgNTAuOTc4IDUwLjk3OCIgc3R5bGU9ImVuYWJsZS1iYWNrZ3JvdW5kOm5ldyAwIDAgNTAuOTc4IDUwLjk3ODsiIHhtbDpzcGFjZT0icHJlc2VydmUiPg0KPGc+DQoJPGc+DQoJCTxnPg0KCQkJPHBhdGggc3R5bGU9ImZpbGw6IzAxMDAwMjsiIGQ9Ik00My41Miw3LjQ1OEMzOC43MTEsMi42NDgsMzIuMzA3LDAsMjUuNDg5LDBDMTguNjcsMCwxMi4yNjYsMi42NDgsNy40NTgsNy40NTgNCgkJCQljLTkuOTQzLDkuOTQxLTkuOTQzLDI2LjExOSwwLDM2LjA2MmM0LjgwOSw0LjgwOSwxMS4yMTIsNy40NTYsMTguMDMxLDcuNDU4YzAsMCwwLjAwMSwwLDAuMDAyLDANCgkJCQljNi44MTYsMCwxMy4yMjEtMi42NDgsMTguMDI5LTcuNDU4YzQuODA5LTQuODA5LDcuNDU3LTExLjIxMiw3LjQ1Ny0xOC4wM0M1MC45NzcsMTguNjcsNDguMzI4LDEyLjI2Niw0My41Miw3LjQ1OHoNCgkJCQkgTTQyLjEwNiw0Mi4xMDVjLTQuNDMyLDQuNDMxLTEwLjMzMiw2Ljg3Mi0xNi42MTUsNi44NzJoLTAuMDAyYy02LjI4NS0wLjAwMS0xMi4xODctMi40NDEtMTYuNjE3LTYuODcyDQoJCQkJYy05LjE2Mi05LjE2My05LjE2Mi0yNC4wNzEsMC0zMy4yMzNDMTMuMzAzLDQuNDQsMTkuMjA0LDIsMjUuNDg5LDJjNi4yODQsMCwxMi4xODYsMi40NCwxNi42MTcsNi44NzINCgkJCQljNC40MzEsNC40MzEsNi44NzEsMTAuMzMyLDYuODcxLDE2LjYxN0M0OC45NzcsMzEuNzcyLDQ2LjUzNiwzNy42NzUsNDIuMTA2LDQyLjEwNXoiLz4NCgkJPC9nPg0KCQk8Zz4NCgkJCTxwYXRoIHN0eWxlPSJmaWxsOiMwMTAwMDI7IiBkPSJNMjMuNTc4LDMyLjIxOGMtMC4wMjMtMS43MzQsMC4xNDMtMy4wNTksMC40OTYtMy45NzJjMC4zNTMtMC45MTMsMS4xMS0xLjk5NywyLjI3Mi0zLjI1Mw0KCQkJCWMwLjQ2OC0wLjUzNiwwLjkyMy0xLjA2MiwxLjM2Ny0xLjU3NWMwLjYyNi0wLjc1MywxLjEwNC0xLjQ3OCwxLjQzNi0yLjE3NWMwLjMzMS0wLjcwNywwLjQ5NS0xLjU0MSwwLjQ5NS0yLjUNCgkJCQljMC0xLjA5Ni0wLjI2LTIuMDg4LTAuNzc5LTIuOTc5Yy0wLjU2NS0wLjg3OS0xLjUwMS0xLjMzNi0yLjgwNi0xLjM2OWMtMS44MDIsMC4wNTctMi45ODUsMC42NjctMy41NSwxLjgzMg0KCQkJCWMtMC4zMDEsMC41MzUtMC41MDMsMS4xNDEtMC42MDcsMS44MTRjLTAuMTM5LDAuNzA3LTAuMjA3LDEuNDMyLTAuMjA3LDIuMTc0aC0yLjkzN2MtMC4wOTEtMi4yMDgsMC40MDctNC4xMTQsMS40OTMtNS43MTkNCgkJCQljMS4wNjItMS42NCwyLjg1NS0yLjQ4MSw1LjM3OC0yLjUyN2MyLjE2LDAuMDIzLDMuODc0LDAuNjA4LDUuMTQxLDEuNzU4YzEuMjc4LDEuMTYsMS45MjksMi43NjQsMS45NSw0LjgxMQ0KCQkJCWMwLDEuMTQyLTAuMTM3LDIuMTExLTAuNDEsMi45MTFjLTAuMzA5LDAuODQ1LTAuNzMxLDEuNTkzLTEuMjY4LDIuMjQzYy0wLjQ5MiwwLjY1LTEuMDY4LDEuMzE4LTEuNzMsMi4wMDINCgkJCQljLTAuNjUsMC42OTctMS4zMTMsMS40NzktMS45ODcsMi4zNDZjLTAuMjM5LDAuMzc3LTAuNDI5LDAuNzc3LTAuNTY1LDEuMTk5Yy0wLjE2LDAuOTU5LTAuMjE3LDEuOTUxLTAuMTcxLDIuOTc5DQoJCQkJQzI2LjU4OSwzMi4yMTgsMjMuNTc4LDMyLjIxOCwyMy41NzgsMzIuMjE4eiBNMjMuNTc4LDM4LjIydi0zLjQ4NGgzLjA3NnYzLjQ4NEgyMy41Nzh6Ii8+DQoJCTwvZz4NCgk8L2c+DQo8L2c+DQo8Zz4NCjwvZz4NCjxnPg0KPC9nPg0KPGc+DQo8L2c+DQo8Zz4NCjwvZz4NCjxnPg0KPC9nPg0KPGc+DQo8L2c+DQo8Zz4NCjwvZz4NCjxnPg0KPC9nPg0KPGc+DQo8L2c+DQo8Zz4NCjwvZz4NCjxnPg0KPC9nPg0KPGc+DQo8L2c+DQo8Zz4NCjwvZz4NCjxnPg0KPC9nPg0KPGc+DQo8L2c+DQo8L3N2Zz4NCg==);
    --jp-icon-markdown: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1jb250cmFzdDAganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjN0IxRkEyIiBkPSJNNSAxNC45aDEybC02LjEgNnptOS40LTYuOGMwLTEuMy0uMS0yLjktLjEtNC41LS40IDEuNC0uOSAyLjktMS4zIDQuM2wtMS4zIDQuM2gtMkw4LjUgNy45Yy0uNC0xLjMtLjctMi45LTEtNC4zLS4xIDEuNi0uMSAzLjItLjIgNC42TDcgMTIuNEg0LjhsLjctMTFoMy4zTDEwIDVjLjQgMS4yLjcgMi43IDEgMy45LjMtMS4yLjctMi42IDEtMy45bDEuMi0zLjdoMy4zbC42IDExaC0yLjRsLS4zLTQuMnoiLz4KPC9zdmc+Cg==);
    --jp-icon-new-folder: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTIwIDZoLThsLTItMkg0Yy0xLjExIDAtMS45OS44OS0xLjk5IDJMMiAxOGMwIDEuMTEuODkgMiAyIDJoMTZjMS4xMSAwIDItLjg5IDItMlY4YzAtMS4xMS0uODktMi0yLTJ6bS0xIDhoLTN2M2gtMnYtM2gtM3YtMmgzVjloMnYzaDN2MnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
    --jp-icon-not-trusted: url(data:image/svg+xml;base64,PHN2ZyBmaWxsPSJub25lIiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI1IDI1Ij4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uMiIgc3Ryb2tlPSIjMzMzMzMzIiBzdHJva2Utd2lkdGg9IjIiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDMgMykiIGQ9Ik0xLjg2MDk0IDExLjQ0MDlDMC44MjY0NDggOC43NzAyNyAwLjg2Mzc3OSA2LjA1NzY0IDEuMjQ5MDcgNC4xOTkzMkMyLjQ4MjA2IDMuOTMzNDcgNC4wODA2OCAzLjQwMzQ3IDUuNjAxMDIgMi44NDQ5QzcuMjM1NDkgMi4yNDQ0IDguODU2NjYgMS41ODE1IDkuOTg3NiAxLjA5NTM5QzExLjA1OTcgMS41ODM0MSAxMi42MDk0IDIuMjQ0NCAxNC4yMTggMi44NDMzOUMxNS43NTAzIDMuNDEzOTQgMTcuMzk5NSAzLjk1MjU4IDE4Ljc1MzkgNC4yMTM4NUMxOS4xMzY0IDYuMDcxNzcgMTkuMTcwOSA4Ljc3NzIyIDE4LjEzOSAxMS40NDA5QzE3LjAzMDMgMTQuMzAzMiAxNC42NjY4IDE3LjE4NDQgOS45OTk5OSAxOC45MzU0QzUuMzMzMTkgMTcuMTg0NCAyLjk2OTY4IDE0LjMwMzIgMS44NjA5NCAxMS40NDA5WiIvPgogICAgPHBhdGggY2xhc3M9ImpwLWljb24yIiBzdHJva2U9IiMzMzMzMzMiIHN0cm9rZS13aWR0aD0iMiIgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoOS4zMTU5MiA5LjMyMDMxKSIgZD0iTTcuMzY4NDIgMEwwIDcuMzY0NzkiLz4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uMiIgc3Ryb2tlPSIjMzMzMzMzIiBzdHJva2Utd2lkdGg9IjIiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDkuMzE1OTIgMTYuNjgzNikgc2NhbGUoMSAtMSkiIGQ9Ik03LjM2ODQyIDBMMCA3LjM2NDc5Ii8+Cjwvc3ZnPgo=);
    --jp-icon-notebook: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8ZyBjbGFzcz0ianAtaWNvbi13YXJuMCBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiNFRjZDMDAiPgogICAgPHBhdGggZD0iTTE4LjcgMy4zdjE1LjRIMy4zVjMuM2gxNS40bTEuNS0xLjVIMS44djE4LjNoMTguM2wuMS0xOC4zeiIvPgogICAgPHBhdGggZD0iTTE2LjUgMTYuNWwtNS40LTQuMy01LjYgNC4zdi0xMWgxMXoiLz4KICA8L2c+Cjwvc3ZnPgo=);
    --jp-icon-numbering: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjIiIGhlaWdodD0iMjIiIHZpZXdCb3g9IjAgMCAyOCAyOCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CgkJPHBhdGggZD0iTTQgMTlINlYxOS41SDVWMjAuNUg2VjIxSDRWMjJIN1YxOEg0VjE5Wk01IDEwSDZWNkg0VjdINVYxMFpNNCAxM0g1LjhMNCAxNS4xVjE2SDdWMTVINS4yTDcgMTIuOVYxMkg0VjEzWk05IDdWOUgyM1Y3SDlaTTkgMjFIMjNWMTlIOVYyMVpNOSAxNUgyM1YxM0g5VjE1WiIvPgoJPC9nPgo8L3N2Zz4K);
    --jp-icon-offline-bolt: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCIgd2lkdGg9IjE2Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEyIDIuMDJjLTUuNTEgMC05Ljk4IDQuNDctOS45OCA5Ljk4czQuNDcgOS45OCA5Ljk4IDkuOTggOS45OC00LjQ3IDkuOTgtOS45OFMxNy41MSAyLjAyIDEyIDIuMDJ6TTExLjQ4IDIwdi02LjI2SDhMMTMgNHY2LjI2aDMuMzVMMTEuNDggMjB6Ii8+CiAgPC9nPgo8L3N2Zz4K);
    --jp-icon-palette: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTE4IDEzVjIwSDRWNkg5LjAyQzkuMDcgNS4yOSA5LjI0IDQuNjIgOS41IDRINEMyLjkgNCAyIDQuOSAyIDZWMjBDMiAyMS4xIDIuOSAyMiA0IDIySDE4QzE5LjEgMjIgMjAgMjEuMSAyMCAyMFYxNUwxOCAxM1pNMTkuMyA4Ljg5QzE5Ljc0IDguMTkgMjAgNy4zOCAyMCA2LjVDMjAgNC4wMSAxNy45OSAyIDE1LjUgMkMxMy4wMSAyIDExIDQuMDEgMTEgNi41QzExIDguOTkgMTMuMDEgMTEgMTUuNDkgMTFDMTYuMzcgMTEgMTcuMTkgMTAuNzQgMTcuODggMTAuM0wyMSAxMy40MkwyMi40MiAxMkwxOS4zIDguODlaTTE1LjUgOUMxNC4xMiA5IDEzIDcuODggMTMgNi41QzEzIDUuMTIgMTQuMTIgNCAxNS41IDRDMTYuODggNCAxOCA1LjEyIDE4IDYuNUMxOCA3Ljg4IDE2Ljg4IDkgMTUuNSA5WiIvPgogICAgPHBhdGggZmlsbC1ydWxlPSJldmVub2RkIiBjbGlwLXJ1bGU9ImV2ZW5vZGQiIGQ9Ik00IDZIOS4wMTg5NEM5LjAwNjM5IDYuMTY1MDIgOSA2LjMzMTc2IDkgNi41QzkgOC44MTU3NyAxMC4yMTEgMTAuODQ4NyAxMi4wMzQzIDEySDlWMTRIMTZWMTIuOTgxMUMxNi41NzAzIDEyLjkzNzcgMTcuMTIgMTIuODIwNyAxNy42Mzk2IDEyLjYzOTZMMTggMTNWMjBINFY2Wk04IDhINlYxMEg4VjhaTTYgMTJIOFYxNEg2VjEyWk04IDE2SDZWMThIOFYxNlpNOSAxNkgxNlYxOEg5VjE2WiIvPgogIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-paste: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTE5IDJoLTQuMThDMTQuNC44NCAxMy4zIDAgMTIgMGMtMS4zIDAtMi40Ljg0LTIuODIgMkg1Yy0xLjEgMC0yIC45LTIgMnYxNmMwIDEuMS45IDIgMiAyaDE0YzEuMSAwIDItLjkgMi0yVjRjMC0xLjEtLjktMi0yLTJ6bS03IDBjLjU1IDAgMSAuNDUgMSAxcy0uNDUgMS0xIDEtMS0uNDUtMS0xIC40NS0xIDEtMXptNyAxOEg1VjRoMnYzaDEwVjRoMnYxNnoiLz4KICAgIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-pdf: url(data:image/svg+xml;base64,PHN2ZwogICB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyMiAyMiIgd2lkdGg9IjE2Ij4KICAgIDxwYXRoIHRyYW5zZm9ybT0icm90YXRlKDQ1KSIgY2xhc3M9ImpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iI0ZGMkEyQSIKICAgICAgIGQ9Im0gMjIuMzQ0MzY5LC0zLjAxNjM2NDIgaCA1LjYzODYwNCB2IDEuNTc5MjQzMyBoIC0zLjU0OTIyNyB2IDEuNTA4NjkyOTkgaCAzLjMzNzU3NiBWIDEuNjUwODE1NCBoIC0zLjMzNzU3NiB2IDMuNDM1MjYxMyBoIC0yLjA4OTM3NyB6IG0gLTcuMTM2NDQ0LDEuNTc5MjQzMyB2IDQuOTQzOTU0MyBoIDAuNzQ4OTIgcSAxLjI4MDc2MSwwIDEuOTUzNzAzLC0wLjYzNDk1MzUgMC42NzgzNjksLTAuNjM0OTUzNSAwLjY3ODM2OSwtMS44NDUxNjQxIDAsLTEuMjA0NzgzNTUgLTAuNjcyOTQyLC0xLjgzNDMxMDExIC0wLjY3Mjk0MiwtMC42Mjk1MjY1OSAtMS45NTkxMywtMC42Mjk1MjY1OSB6IG0gLTIuMDg5Mzc3LC0xLjU3OTI0MzMgaCAyLjIwMzM0MyBxIDEuODQ1MTY0LDAgMi43NDYwMzksMC4yNjU5MjA3IDAuOTA2MzAxLDAuMjYwNDkzNyAxLjU1MjEwOCwwLjg5MDAyMDMgMC41Njk4MywwLjU0ODEyMjMgMC44NDY2MDUsMS4yNjQ0ODAwNiAwLjI3Njc3NCwwLjcxNjM1NzgxIDAuMjc2Nzc0LDEuNjIyNjU4OTQgMCwwLjkxNzE1NTEgLTAuMjc2Nzc0LDEuNjM4OTM5OSAtMC4yNzY3NzUsMC43MTYzNTc4IC0wLjg0NjYwNSwxLjI2NDQ4IC0wLjY1MTIzNCwwLjYyOTUyNjYgLTEuNTYyOTYyLDAuODk1NDQ3MyAtMC45MTE3MjgsMC4yNjA0OTM3IC0yLjczNTE4NSwwLjI2MDQ5MzcgaCAtMi4yMDMzNDMgeiBtIC04LjE0NTg1NjUsMCBoIDMuNDY3ODIzIHEgMS41NDY2ODE2LDAgMi4zNzE1Nzg1LDAuNjg5MjIzIDAuODMwMzI0LDAuNjgzNzk2MSAwLjgzMDMyNCwxLjk1MzcwMzE0IDAsMS4yNzUzMzM5NyAtMC44MzAzMjQsMS45NjQ1NTcwNiBRIDkuOTg3MTk2MSwyLjI3NDkxNSA4LjQ0MDUxNDUsMi4yNzQ5MTUgSCA3LjA2MjA2ODQgViA1LjA4NjA3NjcgSCA0Ljk3MjY5MTUgWiBtIDIuMDg5Mzc2OSwxLjUxNDExOTkgdiAyLjI2MzAzOTQzIGggMS4xNTU5NDEgcSAwLjYwNzgxODgsMCAwLjkzODg2MjksLTAuMjkzMDU1NDcgMC4zMzEwNDQxLC0wLjI5ODQ4MjQxIDAuMzMxMDQ0MSwtMC44NDExNzc3MiAwLC0wLjU0MjY5NTMxIC0wLjMzMTA0NDEsLTAuODM1NzUwNzQgLTAuMzMxMDQ0MSwtMC4yOTMwNTU1IC0wLjkzODg2MjksLTAuMjkzMDU1NSB6IgovPgo8L3N2Zz4K);
    --jp-icon-python: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8ZyBjbGFzcz0ianAtaWNvbi1icmFuZDAganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjMEQ0N0ExIj4KICAgIDxwYXRoIGQ9Ik0xMS4xIDYuOVY1LjhINi45YzAtLjUgMC0xLjMuMi0xLjYuNC0uNy44LTEuMSAxLjctMS40IDEuNy0uMyAyLjUtLjMgMy45LS4xIDEgLjEgMS45LjkgMS45IDEuOXY0LjJjMCAuNS0uOSAxLjYtMiAxLjZIOC44Yy0xLjUgMC0yLjQgMS40LTIuNCAyLjh2Mi4ySDQuN0MzLjUgMTUuMSAzIDE0IDMgMTMuMVY5Yy0uMS0xIC42LTIgMS44LTIgMS41LS4xIDYuMy0uMSA2LjMtLjF6Ii8+CiAgICA8cGF0aCBkPSJNMTAuOSAxNS4xdjEuMWg0LjJjMCAuNSAwIDEuMy0uMiAxLjYtLjQuNy0uOCAxLjEtMS43IDEuNC0xLjcuMy0yLjUuMy0zLjkuMS0xLS4xLTEuOS0uOS0xLjktMS45di00LjJjMC0uNS45LTEuNiAyLTEuNmgzLjhjMS41IDAgMi40LTEuNCAyLjQtMi44VjYuNmgxLjdDMTguNSA2LjkgMTkgOCAxOSA4LjlWMTNjMCAxLS43IDIuMS0xLjkgMi4xaC02LjJ6Ii8+CiAgPC9nPgo8L3N2Zz4K);
    --jp-icon-r-kernel: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1jb250cmFzdDMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjMjE5NkYzIiBkPSJNNC40IDIuNWMxLjItLjEgMi45LS4zIDQuOS0uMyAyLjUgMCA0LjEuNCA1LjIgMS4zIDEgLjcgMS41IDEuOSAxLjUgMy41IDAgMi0xLjQgMy41LTIuOSA0LjEgMS4yLjQgMS43IDEuNiAyLjIgMyAuNiAxLjkgMSAzLjkgMS4zIDQuNmgtMy44Yy0uMy0uNC0uOC0xLjctMS4yLTMuN3MtMS4yLTIuNi0yLjYtMi42aC0uOXY2LjRINC40VjIuNXptMy43IDYuOWgxLjRjMS45IDAgMi45LS45IDIuOS0yLjNzLTEtMi4zLTIuOC0yLjNjLS43IDAtMS4zIDAtMS42LjJ2NC41aC4xdi0uMXoiLz4KPC9zdmc+Cg==);
    --jp-icon-react: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMTUwIDE1MCA1NDEuOSAyOTUuMyI+CiAgPGcgY2xhc3M9ImpwLWljb24tYnJhbmQyIGpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iIzYxREFGQiI+CiAgICA8cGF0aCBkPSJNNjY2LjMgMjk2LjVjMC0zMi41LTQwLjctNjMuMy0xMDMuMS04Mi40IDE0LjQtNjMuNiA4LTExNC4yLTIwLjItMTMwLjQtNi41LTMuOC0xNC4xLTUuNi0yMi40LTUuNnYyMi4zYzQuNiAwIDguMy45IDExLjQgMi42IDEzLjYgNy44IDE5LjUgMzcuNSAxNC45IDc1LjctMS4xIDkuNC0yLjkgMTkuMy01LjEgMjkuNC0xOS42LTQuOC00MS04LjUtNjMuNS0xMC45LTEzLjUtMTguNS0yNy41LTM1LjMtNDEuNi01MCAzMi42LTMwLjMgNjMuMi00Ni45IDg0LTQ2LjlWNzhjLTI3LjUgMC02My41IDE5LjYtOTkuOSA1My42LTM2LjQtMzMuOC03Mi40LTUzLjItOTkuOS01My4ydjIyLjNjMjAuNyAwIDUxLjQgMTYuNSA4NCA0Ni42LTE0IDE0LjctMjggMzEuNC00MS4zIDQ5LjktMjIuNiAyLjQtNDQgNi4xLTYzLjYgMTEtMi4zLTEwLTQtMTkuNy01LjItMjktNC43LTM4LjIgMS4xLTY3LjkgMTQuNi03NS44IDMtMS44IDYuOS0yLjYgMTEuNS0yLjZWNzguNWMtOC40IDAtMTYgMS44LTIyLjYgNS42LTI4LjEgMTYuMi0zNC40IDY2LjctMTkuOSAxMzAuMS02Mi4yIDE5LjItMTAyLjcgNDkuOS0xMDIuNyA4Mi4zIDAgMzIuNSA0MC43IDYzLjMgMTAzLjEgODIuNC0xNC40IDYzLjYtOCAxMTQuMiAyMC4yIDEzMC40IDYuNSAzLjggMTQuMSA1LjYgMjIuNSA1LjYgMjcuNSAwIDYzLjUtMTkuNiA5OS45LTUzLjYgMzYuNCAzMy44IDcyLjQgNTMuMiA5OS45IDUzLjIgOC40IDAgMTYtMS44IDIyLjYtNS42IDI4LjEtMTYuMiAzNC40LTY2LjcgMTkuOS0xMzAuMSA2Mi0xOS4xIDEwMi41LTQ5LjkgMTAyLjUtODIuM3ptLTEzMC4yLTY2LjdjLTMuNyAxMi45LTguMyAyNi4yLTEzLjUgMzkuNS00LjEtOC04LjQtMTYtMTMuMS0yNC00LjYtOC05LjUtMTUuOC0xNC40LTIzLjQgMTQuMiAyLjEgMjcuOSA0LjcgNDEgNy45em0tNDUuOCAxMDYuNWMtNy44IDEzLjUtMTUuOCAyNi4zLTI0LjEgMzguMi0xNC45IDEuMy0zMCAyLTQ1LjIgMi0xNS4xIDAtMzAuMi0uNy00NS0xLjktOC4zLTExLjktMTYuNC0yNC42LTI0LjItMzgtNy42LTEzLjEtMTQuNS0yNi40LTIwLjgtMzkuOCA2LjItMTMuNCAxMy4yLTI2LjggMjAuNy0zOS45IDcuOC0xMy41IDE1LjgtMjYuMyAyNC4xLTM4LjIgMTQuOS0xLjMgMzAtMiA0NS4yLTIgMTUuMSAwIDMwLjIuNyA0NSAxLjkgOC4zIDExLjkgMTYuNCAyNC42IDI0LjIgMzggNy42IDEzLjEgMTQuNSAyNi40IDIwLjggMzkuOC02LjMgMTMuNC0xMy4yIDI2LjgtMjAuNyAzOS45em0zMi4zLTEzYzUuNCAxMy40IDEwIDI2LjggMTMuOCAzOS44LTEzLjEgMy4yLTI2LjkgNS45LTQxLjIgOCA0LjktNy43IDkuOC0xNS42IDE0LjQtMjMuNyA0LjYtOCA4LjktMTYuMSAxMy0yNC4xek00MjEuMiA0MzBjLTkuMy05LjYtMTguNi0yMC4zLTI3LjgtMzIgOSAuNCAxOC4yLjcgMjcuNS43IDkuNCAwIDE4LjctLjIgMjcuOC0uNy05IDExLjctMTguMyAyMi40LTI3LjUgMzJ6bS03NC40LTU4LjljLTE0LjItMi4xLTI3LjktNC43LTQxLTcuOSAzLjctMTIuOSA4LjMtMjYuMiAxMy41LTM5LjUgNC4xIDggOC40IDE2IDEzLjEgMjQgNC43IDggOS41IDE1LjggMTQuNCAyMy40ek00MjAuNyAxNjNjOS4zIDkuNiAxOC42IDIwLjMgMjcuOCAzMi05LS40LTE4LjItLjctMjcuNS0uNy05LjQgMC0xOC43LjItMjcuOC43IDktMTEuNyAxOC4zLTIyLjQgMjcuNS0zMnptLTc0IDU4LjljLTQuOSA3LjctOS44IDE1LjYtMTQuNCAyMy43LTQuNiA4LTguOSAxNi0xMyAyNC01LjQtMTMuNC0xMC0yNi44LTEzLjgtMzkuOCAxMy4xLTMuMSAyNi45LTUuOCA0MS4yLTcuOXptLTkwLjUgMTI1LjJjLTM1LjQtMTUuMS01OC4zLTM0LjktNTguMy01MC42IDAtMTUuNyAyMi45LTM1LjYgNTguMy01MC42IDguNi0zLjcgMTgtNyAyNy43LTEwLjEgNS43IDE5LjYgMTMuMiA0MCAyMi41IDYwLjktOS4yIDIwLjgtMTYuNiA0MS4xLTIyLjIgNjAuNi05LjktMy4xLTE5LjMtNi41LTI4LTEwLjJ6TTMxMCA0OTBjLTEzLjYtNy44LTE5LjUtMzcuNS0xNC45LTc1LjcgMS4xLTkuNCAyLjktMTkuMyA1LjEtMjkuNCAxOS42IDQuOCA0MSA4LjUgNjMuNSAxMC45IDEzLjUgMTguNSAyNy41IDM1LjMgNDEuNiA1MC0zMi42IDMwLjMtNjMuMiA0Ni45LTg0IDQ2LjktNC41LS4xLTguMy0xLTExLjMtMi43em0yMzcuMi03Ni4yYzQuNyAzOC4yLTEuMSA2Ny45LTE0LjYgNzUuOC0zIDEuOC02LjkgMi42LTExLjUgMi42LTIwLjcgMC01MS40LTE2LjUtODQtNDYuNiAxNC0xNC43IDI4LTMxLjQgNDEuMy00OS45IDIyLjYtMi40IDQ0LTYuMSA2My42LTExIDIuMyAxMC4xIDQuMSAxOS44IDUuMiAyOS4xem0zOC41LTY2LjdjLTguNiAzLjctMTggNy0yNy43IDEwLjEtNS43LTE5LjYtMTMuMi00MC0yMi41LTYwLjkgOS4yLTIwLjggMTYuNi00MS4xIDIyLjItNjAuNiA5LjkgMy4xIDE5LjMgNi41IDI4LjEgMTAuMiAzNS40IDE1LjEgNTguMyAzNC45IDU4LjMgNTAuNi0uMSAxNS43LTIzIDM1LjYtNTguNCA1MC42ek0zMjAuOCA3OC40eiIvPgogICAgPGNpcmNsZSBjeD0iNDIwLjkiIGN5PSIyOTYuNSIgcj0iNDUuNyIvPgogIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-redo: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIGhlaWdodD0iMjQiIHZpZXdCb3g9IjAgMCAyNCAyNCIgd2lkdGg9IjE2Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgICA8cGF0aCBkPSJNMCAwaDI0djI0SDB6IiBmaWxsPSJub25lIi8+PHBhdGggZD0iTTE4LjQgMTAuNkMxNi41NSA4Ljk5IDE0LjE1IDggMTEuNSA4Yy00LjY1IDAtOC41OCAzLjAzLTkuOTYgNy4yMkwzLjkgMTZjMS4wNS0zLjE5IDQuMDUtNS41IDcuNi01LjUgMS45NSAwIDMuNzMuNzIgNS4xMiAxLjg4TDEzIDE2aDlWN2wtMy42IDMuNnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
    --jp-icon-refresh: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTkgMTMuNWMtMi40OSAwLTQuNS0yLjAxLTQuNS00LjVTNi41MSA0LjUgOSA0LjVjMS4yNCAwIDIuMzYuNTIgMy4xNyAxLjMzTDEwIDhoNVYzbC0xLjc2IDEuNzZDMTIuMTUgMy42OCAxMC42NiAzIDkgMyA1LjY5IDMgMy4wMSA1LjY5IDMuMDEgOVM1LjY5IDE1IDkgMTVjMi45NyAwIDUuNDMtMi4xNiA1LjktNWgtMS41MmMtLjQ2IDItMi4yNCAzLjUtNC4zOCAzLjV6Ii8+CiAgICA8L2c+Cjwvc3ZnPgo=);
    --jp-icon-regex: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwIDIwIj4KICA8ZyBjbGFzcz0ianAtaWNvbjIiIGZpbGw9IiM0MTQxNDEiPgogICAgPHJlY3QgeD0iMiIgeT0iMiIgd2lkdGg9IjE2IiBoZWlnaHQ9IjE2Ii8+CiAgPC9nPgoKICA8ZyBjbGFzcz0ianAtaWNvbi1hY2NlbnQyIiBmaWxsPSIjRkZGIj4KICAgIDxjaXJjbGUgY2xhc3M9InN0MiIgY3g9IjUuNSIgY3k9IjE0LjUiIHI9IjEuNSIvPgogICAgPHJlY3QgeD0iMTIiIHk9IjQiIGNsYXNzPSJzdDIiIHdpZHRoPSIxIiBoZWlnaHQ9IjgiLz4KICAgIDxyZWN0IHg9IjguNSIgeT0iNy41IiB0cmFuc2Zvcm09Im1hdHJpeCgwLjg2NiAtMC41IDAuNSAwLjg2NiAtMi4zMjU1IDcuMzIxOSkiIGNsYXNzPSJzdDIiIHdpZHRoPSI4IiBoZWlnaHQ9IjEiLz4KICAgIDxyZWN0IHg9IjEyIiB5PSI0IiB0cmFuc2Zvcm09Im1hdHJpeCgwLjUgLTAuODY2IDAuODY2IDAuNSAtMC42Nzc5IDE0LjgyNTIpIiBjbGFzcz0ic3QyIiB3aWR0aD0iMSIgaGVpZ2h0PSI4Ii8+CiAgPC9nPgo8L3N2Zz4K);
    --jp-icon-run: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTggNXYxNGwxMS03eiIvPgogICAgPC9nPgo8L3N2Zz4K);
    --jp-icon-running: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDUxMiA1MTIiPgogIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICA8cGF0aCBkPSJNMjU2IDhDMTE5IDggOCAxMTkgOCAyNTZzMTExIDI0OCAyNDggMjQ4IDI0OC0xMTEgMjQ4LTI0OFMzOTMgOCAyNTYgOHptOTYgMzI4YzAgOC44LTcuMiAxNi0xNiAxNkgxNzZjLTguOCAwLTE2LTcuMi0xNi0xNlYxNzZjMC04LjggNy4yLTE2IDE2LTE2aDE2MGM4LjggMCAxNiA3LjIgMTYgMTZ2MTYweiIvPgogIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-save: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTE3IDNINWMtMS4xMSAwLTIgLjktMiAydjE0YzAgMS4xLjg5IDIgMiAyaDE0YzEuMSAwIDItLjkgMi0yVjdsLTQtNHptLTUgMTZjLTEuNjYgMC0zLTEuMzQtMy0zczEuMzQtMyAzLTMgMyAxLjM0IDMgMy0xLjM0IDMtMyAzem0zLTEwSDVWNWgxMHY0eiIvPgogICAgPC9nPgo8L3N2Zz4K);
    --jp-icon-search: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMTggMTgiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEyLjEsMTAuOWgtMC43bC0wLjItMC4yYzAuOC0wLjksMS4zLTIuMiwxLjMtMy41YzAtMy0yLjQtNS40LTUuNC01LjRTMS44LDQuMiwxLjgsNy4xczIuNCw1LjQsNS40LDUuNCBjMS4zLDAsMi41LTAuNSwzLjUtMS4zbDAuMiwwLjJ2MC43bDQuMSw0LjFsMS4yLTEuMkwxMi4xLDEwLjl6IE03LjEsMTAuOWMtMi4xLDAtMy43LTEuNy0zLjctMy43czEuNy0zLjcsMy43LTMuN3MzLjcsMS43LDMuNywzLjcgUzkuMiwxMC45LDcuMSwxMC45eiIvPgogIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-settings: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMTkuNDMgMTIuOThjLjA0LS4zMi4wNy0uNjQuMDctLjk4cy0uMDMtLjY2LS4wNy0uOThsMi4xMS0xLjY1Yy4xOS0uMTUuMjQtLjQyLjEyLS42NGwtMi0zLjQ2Yy0uMTItLjIyLS4zOS0uMy0uNjEtLjIybC0yLjQ5IDFjLS41Mi0uNC0xLjA4LS43My0xLjY5LS45OGwtLjM4LTIuNjVBLjQ4OC40ODggMCAwMDE0IDJoLTRjLS4yNSAwLS40Ni4xOC0uNDkuNDJsLS4zOCAyLjY1Yy0uNjEuMjUtMS4xNy41OS0xLjY5Ljk4bC0yLjQ5LTFjLS4yMy0uMDktLjQ5IDAtLjYxLjIybC0yIDMuNDZjLS4xMy4yMi0uMDcuNDkuMTIuNjRsMi4xMSAxLjY1Yy0uMDQuMzItLjA3LjY1LS4wNy45OHMuMDMuNjYuMDcuOThsLTIuMTEgMS42NWMtLjE5LjE1LS4yNC40Mi0uMTIuNjRsMiAzLjQ2Yy4xMi4yMi4zOS4zLjYxLjIybDIuNDktMWMuNTIuNCAxLjA4LjczIDEuNjkuOThsLjM4IDIuNjVjLjAzLjI0LjI0LjQyLjQ5LjQyaDRjLjI1IDAgLjQ2LS4xOC40OS0uNDJsLjM4LTIuNjVjLjYxLS4yNSAxLjE3LS41OSAxLjY5LS45OGwyLjQ5IDFjLjIzLjA5LjQ5IDAgLjYxLS4yMmwyLTMuNDZjLjEyLS4yMi4wNy0uNDktLjEyLS42NGwtMi4xMS0xLjY1ek0xMiAxNS41Yy0xLjkzIDAtMy41LTEuNTctMy41LTMuNXMxLjU3LTMuNSAzLjUtMy41IDMuNSAxLjU3IDMuNSAzLjUtMS41NyAzLjUtMy41IDMuNXoiLz4KPC9zdmc+Cg==);
    --jp-icon-spreadsheet: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1jb250cmFzdDEganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNENBRjUwIiBkPSJNMi4yIDIuMnYxNy42aDE3LjZWMi4ySDIuMnptMTUuNCA3LjdoLTUuNVY0LjRoNS41djUuNXpNOS45IDQuNHY1LjVINC40VjQuNGg1LjV6bS01LjUgNy43aDUuNXY1LjVINC40di01LjV6bTcuNyA1LjV2LTUuNWg1LjV2NS41aC01LjV6Ii8+Cjwvc3ZnPgo=);
    --jp-icon-stop: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTAgMGgyNHYyNEgweiIgZmlsbD0ibm9uZSIvPgogICAgICAgIDxwYXRoIGQ9Ik02IDZoMTJ2MTJINnoiLz4KICAgIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-tab: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTIxIDNIM2MtMS4xIDAtMiAuOS0yIDJ2MTRjMCAxLjEuOSAyIDIgMmgxOGMxLjEgMCAyLS45IDItMlY1YzAtMS4xLS45LTItMi0yem0wIDE2SDNWNWgxMHY0aDh2MTB6Ii8+CiAgPC9nPgo8L3N2Zz4K);
    --jp-icon-table-rows: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTAgMGgyNHYyNEgweiIgZmlsbD0ibm9uZSIvPgogICAgICAgIDxwYXRoIGQ9Ik0yMSw4SDNWNGgxOFY4eiBNMjEsMTBIM3Y0aDE4VjEweiBNMjEsMTZIM3Y0aDE4VjE2eiIvPgogICAgPC9nPgo8L3N2Zz4=);
    --jp-icon-tag: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjgiIGhlaWdodD0iMjgiIHZpZXdCb3g9IjAgMCA0MyAyOCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CgkJPHBhdGggZD0iTTI4LjgzMzIgMTIuMzM0TDMyLjk5OTggMTYuNTAwN0wzNy4xNjY1IDEyLjMzNEgyOC44MzMyWiIvPgoJCTxwYXRoIGQ9Ik0xNi4yMDk1IDIxLjYxMDRDMTUuNjg3MyAyMi4xMjk5IDE0Ljg0NDMgMjIuMTI5OSAxNC4zMjQ4IDIxLjYxMDRMNi45ODI5IDE0LjcyNDVDNi41NzI0IDE0LjMzOTQgNi4wODMxMyAxMy42MDk4IDYuMDQ3ODYgMTMuMDQ4MkM1Ljk1MzQ3IDExLjUyODggNi4wMjAwMiA4LjYxOTQ0IDYuMDY2MjEgNy4wNzY5NUM2LjA4MjgxIDYuNTE0NzcgNi41NTU0OCA2LjA0MzQ3IDcuMTE4MDQgNi4wMzA1NUM5LjA4ODYzIDUuOTg0NzMgMTMuMjYzOCA1LjkzNTc5IDEzLjY1MTggNi4zMjQyNUwyMS43MzY5IDEzLjYzOUMyMi4yNTYgMTQuMTU4NSAyMS43ODUxIDE1LjQ3MjQgMjEuMjYyIDE1Ljk5NDZMMTYuMjA5NSAyMS42MTA0Wk05Ljc3NTg1IDguMjY1QzkuMzM1NTEgNy44MjU2NiA4LjYyMzUxIDcuODI1NjYgOC4xODI4IDguMjY1QzcuNzQzNDYgOC43MDU3MSA3Ljc0MzQ2IDkuNDE3MzMgOC4xODI4IDkuODU2NjdDOC42MjM4MiAxMC4yOTY0IDkuMzM1ODIgMTAuMjk2NCA5Ljc3NTg1IDkuODU2NjdDMTAuMjE1NiA5LjQxNzMzIDEwLjIxNTYgOC43MDUzMyA5Ljc3NTg1IDguMjY1WiIvPgoJPC9nPgo8L3N2Zz4K);
    --jp-icon-terminal: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0IiA+CiAgICA8cmVjdCBjbGFzcz0ianAtaWNvbjIganAtaWNvbi1zZWxlY3RhYmxlIiB3aWR0aD0iMjAiIGhlaWdodD0iMjAiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDIgMikiIGZpbGw9IiMzMzMzMzMiLz4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uLWFjY2VudDIganAtaWNvbi1zZWxlY3RhYmxlLWludmVyc2UiIGQ9Ik01LjA1NjY0IDguNzYxNzJDNS4wNTY2NCA4LjU5NzY2IDUuMDMxMjUgOC40NTMxMiA0Ljk4MDQ3IDguMzI4MTJDNC45MzM1OSA4LjE5OTIyIDQuODU1NDcgOC4wODIwMyA0Ljc0NjA5IDcuOTc2NTZDNC42NDA2MiA3Ljg3MTA5IDQuNSA3Ljc3NTM5IDQuMzI0MjIgNy42ODk0NUM0LjE1MjM0IDcuNTk5NjEgMy45NDMzNiA3LjUxMTcyIDMuNjk3MjcgNy40MjU3OEMzLjMwMjczIDcuMjg1MTYgMi45NDMzNiA3LjEzNjcyIDIuNjE5MTQgNi45ODA0N0MyLjI5NDkyIDYuODI0MjIgMi4wMTc1OCA2LjY0MjU4IDEuNzg3MTEgNi40MzU1NUMxLjU2MDU1IDYuMjI4NTIgMS4zODQ3NyA1Ljk4ODI4IDEuMjU5NzcgNS43MTQ4NEMxLjEzNDc3IDUuNDM3NSAxLjA3MjI3IDUuMTA5MzggMS4wNzIyNyA0LjczMDQ3QzEuMDcyMjcgNC4zOTg0NCAxLjEyODkxIDQuMDk1NyAxLjI0MjE5IDMuODIyMjdDMS4zNTU0NyAzLjU0NDkyIDEuNTE1NjIgMy4zMDQ2OSAxLjcyMjY2IDMuMTAxNTZDMS45Mjk2OSAyLjg5ODQ0IDIuMTc5NjkgMi43MzQzNyAyLjQ3MjY2IDIuNjA5MzhDMi43NjU2MiAyLjQ4NDM4IDMuMDkxOCAyLjQwNDMgMy40NTExNyAyLjM2OTE0VjEuMTA5MzhINC4zODg2N1YyLjM4MDg2QzQuNzQwMjMgMi40Mjc3MyA1LjA1NjY0IDIuNTIzNDQgNS4zMzc4OSAyLjY2Nzk3QzUuNjE5MTQgMi44MTI1IDUuODU3NDIgMy4wMDE5NSA2LjA1MjczIDMuMjM2MzNDNi4yNTE5NSAzLjQ2NjggNi40MDQzIDMuNzQwMjMgNi41MDk3NyA0LjA1NjY0QzYuNjE5MTQgNC4zNjkxNCA2LjY3MzgzIDQuNzIwNyA2LjY3MzgzIDUuMTExMzNINS4wNDQ5MkM1LjA0NDkyIDQuNjM4NjcgNC45Mzc1IDQuMjgxMjUgNC43MjI2NiA0LjAzOTA2QzQuNTA3ODEgMy43OTI5NyA0LjIxNjggMy42Njk5MiAzLjg0OTYxIDMuNjY5OTJDMy42NTAzOSAzLjY2OTkyIDMuNDc2NTYgMy42OTcyNyAzLjMyODEyIDMuNzUxOTVDMy4xODM1OSAzLjgwMjczIDMuMDY0NDUgMy44NzY5NSAyLjk3MDcgMy45NzQ2MUMyLjg3Njk1IDQuMDY4MzYgMi44MDY2NCA0LjE3OTY5IDIuNzU5NzcgNC4zMDg1OUMyLjcxNjggNC40Mzc1IDIuNjk1MzEgNC41NzgxMiAyLjY5NTMxIDQuNzMwNDdDMi42OTUzMSA0Ljg4MjgxIDIuNzE2OCA1LjAxOTUzIDIuNzU5NzcgNS4xNDA2MkMyLjgwNjY0IDUuMjU3ODEgMi44ODI4MSA1LjM2NzE5IDIuOTg4MjggNS40Njg3NUMzLjA5NzY2IDUuNTcwMzEgMy4yNDAyMyA1LjY2Nzk3IDMuNDE2MDIgNS43NjE3MkMzLjU5MTggNS44NTE1NiAzLjgxMDU1IDUuOTQzMzYgNC4wNzIyNyA2LjAzNzExQzQuNDY2OCA2LjE4NTU1IDQuODI0MjIgNi4zMzk4NCA1LjE0NDUzIDYuNUM1LjQ2NDg0IDYuNjU2MjUgNS43MzgyOCA2LjgzOTg0IDUuOTY0ODQgNy4wNTA3OEM2LjE5NTMxIDcuMjU3ODEgNi4zNzEwOSA3LjUgNi40OTIxOSA3Ljc3NzM0QzYuNjE3MTkgOC4wNTA3OCA2LjY3OTY5IDguMzc1IDYuNjc5NjkgOC43NUM2LjY3OTY5IDkuMDkzNzUgNi42MjMwNSA5LjQwNDMgNi41MDk3NyA5LjY4MTY0QzYuMzk2NDggOS45NTUwOCA2LjIzNDM4IDEwLjE5MTQgNi4wMjM0NCAxMC4zOTA2QzUuODEyNSAxMC41ODk4IDUuNTU4NTkgMTAuNzUgNS4yNjE3MiAxMC44NzExQzQuOTY0ODQgMTAuOTg4MyA0LjYzMjgxIDExLjA2NDUgNC4yNjU2MiAxMS4wOTk2VjEyLjI0OEgzLjMzMzk4VjExLjA5OTZDMy4wMDE5NSAxMS4wNjg0IDIuNjc5NjkgMTAuOTk2MSAyLjM2NzE5IDEwLjg4MjhDMi4wNTQ2OSAxMC43NjU2IDEuNzc3MzQgMTAuNTk3NyAxLjUzNTE2IDEwLjM3ODlDMS4yOTY4OCAxMC4xNjAyIDEuMTA1NDcgOS44ODQ3NyAwLjk2MDkzOCA5LjU1MjczQzAuODE2NDA2IDkuMjE2OCAwLjc0NDE0MSA4LjgxNDQ1IDAuNzQ0MTQxIDguMzQ1N0gyLjM3ODkxQzIuMzc4OTEgOC42MjY5NSAyLjQxOTkyIDguODYzMjggMi41MDE5NSA5LjA1NDY5QzIuNTgzOTggOS4yNDIxOSAyLjY4OTQ1IDkuMzkyNTggMi44MTgzNiA5LjUwNTg2QzIuOTUxMTcgOS42MTUyMyAzLjEwMTU2IDkuNjkzMzYgMy4yNjk1MyA5Ljc0MDIzQzMuNDM3NSA5Ljc4NzExIDMuNjA5MzggOS44MTA1NSAzLjc4NTE2IDkuODEwNTVDNC4yMDMxMiA5LjgxMDU1IDQuNTE5NTMgOS43MTI4OSA0LjczNDM4IDkuNTE3NThDNC45NDkyMiA5LjMyMjI3IDUuMDU2NjQgOS4wNzAzMSA1LjA1NjY0IDguNzYxNzJaTTEzLjQxOCAxMi4yNzE1SDguMDc0MjJWMTFIMTMuNDE4VjEyLjI3MTVaIiB0cmFuc2Zvcm09InRyYW5zbGF0ZSgzLjk1MjY0IDYpIiBmaWxsPSJ3aGl0ZSIvPgo8L3N2Zz4K);
    --jp-icon-text-editor: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMTUgMTVIM3YyaDEydi0yem0wLThIM3YyaDEyVjd6TTMgMTNoMTh2LTJIM3Yyem0wIDhoMTh2LTJIM3Yyek0zIDN2MmgxOFYzSDN6Ii8+Cjwvc3ZnPgo=);
    --jp-icon-toc: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHhtbG5zOnhsaW5rPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5L3hsaW5rIiB2ZXJzaW9uPSIxLjEiIHdpZHRoPSIyNCIgaGVpZ2h0PSIyNCIgdmlld0JveD0iMCAwIDI0IDI0IiBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgoJPHBhdGggZD0iTTcsNUgyMVY3SDdWNU03LDEzVjExSDIxVjEzSDdNNCw0LjVBMS41LDEuNSAwIDAsMSA1LjUsNkExLjUsMS41IDAgMCwxIDQsNy41QTEuNSwxLjUgMCAwLDEgMi41LDZBMS41LDEuNSAwIDAsMSA0LDQuNU00LDEwLjVBMS41LDEuNSAwIDAsMSA1LjUsMTJBMS41LDEuNSAwIDAsMSA0LDEzLjVBMS41LDEuNSAwIDAsMSAyLjUsMTJBMS41LDEuNSAwIDAsMSA0LDEwLjVNNywxOVYxN0gyMVYxOUg3TTQsMTYuNUExLjUsMS41IDAgMCwxIDUuNSwxOEExLjUsMS41IDAgMCwxIDQsMTkuNUExLjUsMS41IDAgMCwxIDIuNSwxOEExLjUsMS41IDAgMCwxIDQsMTYuNVoiIC8+Cjwvc3ZnPgo=);
    --jp-icon-tree-view: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTAgMGgyNHYyNEgweiIgZmlsbD0ibm9uZSIvPgogICAgICAgIDxwYXRoIGQ9Ik0yMiAxMVYzaC03djNIOVYzSDJ2OGg3VjhoMnYxMGg0djNoN3YtOGgtN3YzaC0yVjhoMnYzeiIvPgogICAgPC9nPgo8L3N2Zz4=);
    --jp-icon-trusted: url(data:image/svg+xml;base64,PHN2ZyBmaWxsPSJub25lIiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI1Ij4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uMiIgc3Ryb2tlPSIjMzMzMzMzIiBzdHJva2Utd2lkdGg9IjIiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDIgMykiIGQ9Ik0xLjg2MDk0IDExLjQ0MDlDMC44MjY0NDggOC43NzAyNyAwLjg2Mzc3OSA2LjA1NzY0IDEuMjQ5MDcgNC4xOTkzMkMyLjQ4MjA2IDMuOTMzNDcgNC4wODA2OCAzLjQwMzQ3IDUuNjAxMDIgMi44NDQ5QzcuMjM1NDkgMi4yNDQ0IDguODU2NjYgMS41ODE1IDkuOTg3NiAxLjA5NTM5QzExLjA1OTcgMS41ODM0MSAxMi42MDk0IDIuMjQ0NCAxNC4yMTggMi44NDMzOUMxNS43NTAzIDMuNDEzOTQgMTcuMzk5NSAzLjk1MjU4IDE4Ljc1MzkgNC4yMTM4NUMxOS4xMzY0IDYuMDcxNzcgMTkuMTcwOSA4Ljc3NzIyIDE4LjEzOSAxMS40NDA5QzE3LjAzMDMgMTQuMzAzMiAxNC42NjY4IDE3LjE4NDQgOS45OTk5OSAxOC45MzU0QzUuMzMzMiAxNy4xODQ0IDIuOTY5NjggMTQuMzAzMiAxLjg2MDk0IDExLjQ0MDlaIi8+CiAgICA8cGF0aCBjbGFzcz0ianAtaWNvbjIiIGZpbGw9IiMzMzMzMzMiIHN0cm9rZT0iIzMzMzMzMyIgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoOCA5Ljg2NzE5KSIgZD0iTTIuODYwMTUgNC44NjUzNUwwLjcyNjU0OSAyLjk5OTU5TDAgMy42MzA0NUwyLjg2MDE1IDYuMTMxNTdMOCAwLjYzMDg3Mkw3LjI3ODU3IDBMMi44NjAxNSA0Ljg2NTM1WiIvPgo8L3N2Zz4K);
    --jp-icon-undo: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEyLjUgOGMtMi42NSAwLTUuMDUuOTktNi45IDIuNkwyIDd2OWg5bC0zLjYyLTMuNjJjMS4zOS0xLjE2IDMuMTYtMS44OCA1LjEyLTEuODggMy41NCAwIDYuNTUgMi4zMSA3LjYgNS41bDIuMzctLjc4QzIxLjA4IDExLjAzIDE3LjE1IDggMTIuNSA4eiIvPgogIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-vega: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8ZyBjbGFzcz0ianAtaWNvbjEganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjMjEyMTIxIj4KICAgIDxwYXRoIGQ9Ik0xMC42IDUuNGwyLjItMy4ySDIuMnY3LjNsNC02LjZ6Ii8+CiAgICA8cGF0aCBkPSJNMTUuOCAyLjJsLTQuNCA2LjZMNyA2LjNsLTQuOCA4djUuNWgxNy42VjIuMmgtNHptLTcgMTUuNEg1LjV2LTQuNGgzLjN2NC40em00LjQgMEg5LjhWOS44aDMuNHY3Ljh6bTQuNCAwaC0zLjRWNi41aDMuNHYxMS4xeiIvPgogIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-yaml: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8ZyBjbGFzcz0ianAtaWNvbi1jb250cmFzdDIganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjRDgxQjYwIj4KICAgIDxwYXRoIGQ9Ik03LjIgMTguNnYtNS40TDMgNS42aDMuM2wxLjQgMy4xYy4zLjkuNiAxLjYgMSAyLjUuMy0uOC42LTEuNiAxLTIuNWwxLjQtMy4xaDMuNGwtNC40IDcuNnY1LjVsLTIuOS0uMXoiLz4KICAgIDxjaXJjbGUgY2xhc3M9InN0MCIgY3g9IjE3LjYiIGN5PSIxNi41IiByPSIyLjEiLz4KICAgIDxjaXJjbGUgY2xhc3M9InN0MCIgY3g9IjE3LjYiIGN5PSIxMSIgcj0iMi4xIi8+CiAgPC9nPgo8L3N2Zz4K);
  }

  /* Icon CSS class declarations */

  .jp-AddIcon {
    background-image: var(--jp-icon-add);
  }
  .jp-BugIcon {
    background-image: var(--jp-icon-bug);
  }
  .jp-BuildIcon {
    background-image: var(--jp-icon-build);
  }
  .jp-CaretDownEmptyIcon {
    background-image: var(--jp-icon-caret-down-empty);
  }
  .jp-CaretDownEmptyThinIcon {
    background-image: var(--jp-icon-caret-down-empty-thin);
  }
  .jp-CaretDownIcon {
    background-image: var(--jp-icon-caret-down);
  }
  .jp-CaretLeftIcon {
    background-image: var(--jp-icon-caret-left);
  }
  .jp-CaretRightIcon {
    background-image: var(--jp-icon-caret-right);
  }
  .jp-CaretUpEmptyThinIcon {
    background-image: var(--jp-icon-caret-up-empty-thin);
  }
  .jp-CaretUpIcon {
    background-image: var(--jp-icon-caret-up);
  }
  .jp-CaseSensitiveIcon {
    background-image: var(--jp-icon-case-sensitive);
  }
  .jp-CheckIcon {
    background-image: var(--jp-icon-check);
  }
  .jp-CircleEmptyIcon {
    background-image: var(--jp-icon-circle-empty);
  }
  .jp-CircleIcon {
    background-image: var(--jp-icon-circle);
  }
  .jp-ClearIcon {
    background-image: var(--jp-icon-clear);
  }
  .jp-CloseIcon {
    background-image: var(--jp-icon-close);
  }
  .jp-CodeIcon {
    background-image: var(--jp-icon-code);
  }
  .jp-ConsoleIcon {
    background-image: var(--jp-icon-console);
  }
  .jp-CopyIcon {
    background-image: var(--jp-icon-copy);
  }
  .jp-CutIcon {
    background-image: var(--jp-icon-cut);
  }
  .jp-DownloadIcon {
    background-image: var(--jp-icon-download);
  }
  .jp-EditIcon {
    background-image: var(--jp-icon-edit);
  }
  .jp-EllipsesIcon {
    background-image: var(--jp-icon-ellipses);
  }
  .jp-ExtensionIcon {
    background-image: var(--jp-icon-extension);
  }
  .jp-FastForwardIcon {
    background-image: var(--jp-icon-fast-forward);
  }
  .jp-FileIcon {
    background-image: var(--jp-icon-file);
  }
  .jp-FileUploadIcon {
    background-image: var(--jp-icon-file-upload);
  }
  .jp-FilterListIcon {
    background-image: var(--jp-icon-filter-list);
  }
  .jp-FolderIcon {
    background-image: var(--jp-icon-folder);
  }
  .jp-Html5Icon {
    background-image: var(--jp-icon-html5);
  }
  .jp-ImageIcon {
    background-image: var(--jp-icon-image);
  }
  .jp-InspectorIcon {
    background-image: var(--jp-icon-inspector);
  }
  .jp-JsonIcon {
    background-image: var(--jp-icon-json);
  }
  .jp-JupyterFaviconIcon {
    background-image: var(--jp-icon-jupyter-favicon);
  }
  .jp-JupyterIcon {
    background-image: var(--jp-icon-jupyter);
  }
  .jp-JupyterlabWordmarkIcon {
    background-image: var(--jp-icon-jupyterlab-wordmark);
  }
  .jp-KernelIcon {
    background-image: var(--jp-icon-kernel);
  }
  .jp-KeyboardIcon {
    background-image: var(--jp-icon-keyboard);
  }
  .jp-LauncherIcon {
    background-image: var(--jp-icon-launcher);
  }
  .jp-LineFormIcon {
    background-image: var(--jp-icon-line-form);
  }
  .jp-LinkIcon {
    background-image: var(--jp-icon-link);
  }
  .jp-ListIcon {
    background-image: var(--jp-icon-list);
  }
  .jp-ListingsInfoIcon {
    background-image: var(--jp-icon-listings-info);
  }
  .jp-MarkdownIcon {
    background-image: var(--jp-icon-markdown);
  }
  .jp-NewFolderIcon {
    background-image: var(--jp-icon-new-folder);
  }
  .jp-NotTrustedIcon {
    background-image: var(--jp-icon-not-trusted);
  }
  .jp-NotebookIcon {
    background-image: var(--jp-icon-notebook);
  }
  .jp-NumberingIcon {
    background-image: var(--jp-icon-numbering);
  }
  .jp-OfflineBoltIcon {
    background-image: var(--jp-icon-offline-bolt);
  }
  .jp-PaletteIcon {
    background-image: var(--jp-icon-palette);
  }
  .jp-PasteIcon {
    background-image: var(--jp-icon-paste);
  }
  .jp-PdfIcon {
    background-image: var(--jp-icon-pdf);
  }
  .jp-PythonIcon {
    background-image: var(--jp-icon-python);
  }
  .jp-RKernelIcon {
    background-image: var(--jp-icon-r-kernel);
  }
  .jp-ReactIcon {
    background-image: var(--jp-icon-react);
  }
  .jp-RedoIcon {
    background-image: var(--jp-icon-redo);
  }
  .jp-RefreshIcon {
    background-image: var(--jp-icon-refresh);
  }
  .jp-RegexIcon {
    background-image: var(--jp-icon-regex);
  }
  .jp-RunIcon {
    background-image: var(--jp-icon-run);
  }
  .jp-RunningIcon {
    background-image: var(--jp-icon-running);
  }
  .jp-SaveIcon {
    background-image: var(--jp-icon-save);
  }
  .jp-SearchIcon {
    background-image: var(--jp-icon-search);
  }
  .jp-SettingsIcon {
    background-image: var(--jp-icon-settings);
  }
  .jp-SpreadsheetIcon {
    background-image: var(--jp-icon-spreadsheet);
  }
  .jp-StopIcon {
    background-image: var(--jp-icon-stop);
  }
  .jp-TabIcon {
    background-image: var(--jp-icon-tab);
  }
  .jp-TableRowsIcon {
    background-image: var(--jp-icon-table-rows);
  }
  .jp-TagIcon {
    background-image: var(--jp-icon-tag);
  }
  .jp-TerminalIcon {
    background-image: var(--jp-icon-terminal);
  }
  .jp-TextEditorIcon {
    background-image: var(--jp-icon-text-editor);
  }
  .jp-TocIcon {
    background-image: var(--jp-icon-toc);
  }
  .jp-TreeViewIcon {
    background-image: var(--jp-icon-tree-view);
  }
  .jp-TrustedIcon {
    background-image: var(--jp-icon-trusted);
  }
  .jp-UndoIcon {
    background-image: var(--jp-icon-undo);
  }
  .jp-VegaIcon {
    background-image: var(--jp-icon-vega);
  }
  .jp-YamlIcon {
    background-image: var(--jp-icon-yaml);
  }

  /*-----------------------------------------------------------------------------
  | Copyright (c) Jupyter Development Team.
  | Distributed under the terms of the Modified BSD License.
  |----------------------------------------------------------------------------*/

  /**
  * (DEPRECATED) Support for consuming icons as CSS background images
  */

  :root {
    --jp-icon-search-white: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMTggMTgiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEyLjEsMTAuOWgtMC43bC0wLjItMC4yYzAuOC0wLjksMS4zLTIuMiwxLjMtMy41YzAtMy0yLjQtNS40LTUuNC01LjRTMS44LDQuMiwxLjgsNy4xczIuNCw1LjQsNS40LDUuNCBjMS4zLDAsMi41LTAuNSwzLjUtMS4zbDAuMiwwLjJ2MC43bDQuMSw0LjFsMS4yLTEuMkwxMi4xLDEwLjl6IE03LjEsMTAuOWMtMi4xLDAtMy43LTEuNy0zLjctMy43czEuNy0zLjcsMy43LTMuN3MzLjcsMS43LDMuNywzLjcgUzkuMiwxMC45LDcuMSwxMC45eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  }

  .jp-Icon,
  .jp-MaterialIcon {
    background-position: center;
    background-repeat: no-repeat;
    background-size: 16px;
    min-width: 16px;
    min-height: 16px;
  }

  .jp-Icon-cover {
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
  }

  /**
  * (DEPRECATED) Support for specific CSS icon sizes
  */

  .jp-Icon-16 {
    background-size: 16px;
    min-width: 16px;
    min-height: 16px;
  }

  .jp-Icon-18 {
    background-size: 18px;
    min-width: 18px;
    min-height: 18px;
  }

  .jp-Icon-20 {
    background-size: 20px;
    min-width: 20px;
    min-height: 20px;
  }

  /*-----------------------------------------------------------------------------
  | Copyright (c) Jupyter Development Team.
  | Distributed under the terms of the Modified BSD License.
  |----------------------------------------------------------------------------*/

  /**
  * Support for icons as inline SVG HTMLElements
  */

  /* recolor the primary elements of an icon */
  .jp-icon0[fill] {
    fill: var(--jp-inverse-layout-color0);
  }
  .jp-icon1[fill] {
    fill: var(--jp-inverse-layout-color1);
  }
  .jp-icon2[fill] {
    fill: var(--jp-inverse-layout-color2);
  }
  .jp-icon3[fill] {
    fill: var(--jp-inverse-layout-color3);
  }
  .jp-icon4[fill] {
    fill: var(--jp-inverse-layout-color4);
  }

  .jp-icon0[stroke] {
    stroke: var(--jp-inverse-layout-color0);
  }
  .jp-icon1[stroke] {
    stroke: var(--jp-inverse-layout-color1);
  }
  .jp-icon2[stroke] {
    stroke: var(--jp-inverse-layout-color2);
  }
  .jp-icon3[stroke] {
    stroke: var(--jp-inverse-layout-color3);
  }
  .jp-icon4[stroke] {
    stroke: var(--jp-inverse-layout-color4);
  }
  /* recolor the accent elements of an icon */
  .jp-icon-accent0[fill] {
    fill: var(--jp-layout-color0);
  }
  .jp-icon-accent1[fill] {
    fill: var(--jp-layout-color1);
  }
  .jp-icon-accent2[fill] {
    fill: var(--jp-layout-color2);
  }
  .jp-icon-accent3[fill] {
    fill: var(--jp-layout-color3);
  }
  .jp-icon-accent4[fill] {
    fill: var(--jp-layout-color4);
  }

  .jp-icon-accent0[stroke] {
    stroke: var(--jp-layout-color0);
  }
  .jp-icon-accent1[stroke] {
    stroke: var(--jp-layout-color1);
  }
  .jp-icon-accent2[stroke] {
    stroke: var(--jp-layout-color2);
  }
  .jp-icon-accent3[stroke] {
    stroke: var(--jp-layout-color3);
  }
  .jp-icon-accent4[stroke] {
    stroke: var(--jp-layout-color4);
  }
  /* set the color of an icon to transparent */
  .jp-icon-none[fill] {
    fill: none;
  }

  .jp-icon-none[stroke] {
    stroke: none;
  }
  /* brand icon colors. Same for light and dark */
  .jp-icon-brand0[fill] {
    fill: var(--jp-brand-color0);
  }
  .jp-icon-brand1[fill] {
    fill: var(--jp-brand-color1);
  }
  .jp-icon-brand2[fill] {
    fill: var(--jp-brand-color2);
  }
  .jp-icon-brand3[fill] {
    fill: var(--jp-brand-color3);
  }
  .jp-icon-brand4[fill] {
    fill: var(--jp-brand-color4);
  }

  .jp-icon-brand0[stroke] {
    stroke: var(--jp-brand-color0);
  }
  .jp-icon-brand1[stroke] {
    stroke: var(--jp-brand-color1);
  }
  .jp-icon-brand2[stroke] {
    stroke: var(--jp-brand-color2);
  }
  .jp-icon-brand3[stroke] {
    stroke: var(--jp-brand-color3);
  }
  .jp-icon-brand4[stroke] {
    stroke: var(--jp-brand-color4);
  }
  /* warn icon colors. Same for light and dark */
  .jp-icon-warn0[fill] {
    fill: var(--jp-warn-color0);
  }
  .jp-icon-warn1[fill] {
    fill: var(--jp-warn-color1);
  }
  .jp-icon-warn2[fill] {
    fill: var(--jp-warn-color2);
  }
  .jp-icon-warn3[fill] {
    fill: var(--jp-warn-color3);
  }

  .jp-icon-warn0[stroke] {
    stroke: var(--jp-warn-color0);
  }
  .jp-icon-warn1[stroke] {
    stroke: var(--jp-warn-color1);
  }
  .jp-icon-warn2[stroke] {
    stroke: var(--jp-warn-color2);
  }
  .jp-icon-warn3[stroke] {
    stroke: var(--jp-warn-color3);
  }
  /* icon colors that contrast well with each other and most backgrounds */
  .jp-icon-contrast0[fill] {
    fill: var(--jp-icon-contrast-color0);
  }
  .jp-icon-contrast1[fill] {
    fill: var(--jp-icon-contrast-color1);
  }
  .jp-icon-contrast2[fill] {
    fill: var(--jp-icon-contrast-color2);
  }
  .jp-icon-contrast3[fill] {
    fill: var(--jp-icon-contrast-color3);
  }

  .jp-icon-contrast0[stroke] {
    stroke: var(--jp-icon-contrast-color0);
  }
  .jp-icon-contrast1[stroke] {
    stroke: var(--jp-icon-contrast-color1);
  }
  .jp-icon-contrast2[stroke] {
    stroke: var(--jp-icon-contrast-color2);
  }
  .jp-icon-contrast3[stroke] {
    stroke: var(--jp-icon-contrast-color3);
  }

  /* CSS for icons in selected items in the settings editor */
  #setting-editor .jp-PluginList .jp-mod-selected .jp-icon-selectable[fill] {
    fill: #fff;
  }
  #setting-editor
    .jp-PluginList
    .jp-mod-selected
    .jp-icon-selectable-inverse[fill] {
    fill: var(--jp-brand-color1);
  }

  /* CSS for icons in selected filebrowser listing items */
  .jp-DirListing-item.jp-mod-selected .jp-icon-selectable[fill] {
    fill: #fff;
  }
  .jp-DirListing-item.jp-mod-selected .jp-icon-selectable-inverse[fill] {
    fill: var(--jp-brand-color1);
  }

  /* CSS for icons in selected tabs in the sidebar tab manager */
  #tab-manager .lm-TabBar-tab.jp-mod-active .jp-icon-selectable[fill] {
    fill: #fff;
  }

  #tab-manager .lm-TabBar-tab.jp-mod-active .jp-icon-selectable-inverse[fill] {
    fill: var(--jp-brand-color1);
  }
  #tab-manager
    .lm-TabBar-tab.jp-mod-active
    .jp-icon-hover
    :hover
    .jp-icon-selectable[fill] {
    fill: var(--jp-brand-color1);
  }

  #tab-manager
    .lm-TabBar-tab.jp-mod-active
    .jp-icon-hover
    :hover
    .jp-icon-selectable-inverse[fill] {
    fill: #fff;
  }

  /**
  * TODO: come up with non css-hack solution for showing the busy icon on top
  *  of the close icon
  * CSS for complex behavior of close icon of tabs in the sidebar tab manager
  */
  #tab-manager
    .lm-TabBar-tab.jp-mod-dirty
    > .lm-TabBar-tabCloseIcon
    > :not(:hover)
    > .jp-icon3[fill] {
    fill: none;
  }
  #tab-manager
    .lm-TabBar-tab.jp-mod-dirty
    > .lm-TabBar-tabCloseIcon
    > :not(:hover)
    > .jp-icon-busy[fill] {
    fill: var(--jp-inverse-layout-color3);
  }

  #tab-manager
    .lm-TabBar-tab.jp-mod-dirty.jp-mod-active
    > .lm-TabBar-tabCloseIcon
    > :not(:hover)
    > .jp-icon-busy[fill] {
    fill: #fff;
  }

  /**
  * TODO: come up with non css-hack solution for showing the busy icon on top
  *  of the close icon
  * CSS for complex behavior of close icon of tabs in the main area tabbar
  */
  .lm-DockPanel-tabBar
    .lm-TabBar-tab.lm-mod-closable.jp-mod-dirty
    > .lm-TabBar-tabCloseIcon
    > :not(:hover)
    > .jp-icon3[fill] {
    fill: none;
  }
  .lm-DockPanel-tabBar
    .lm-TabBar-tab.lm-mod-closable.jp-mod-dirty
    > .lm-TabBar-tabCloseIcon
    > :not(:hover)
    > .jp-icon-busy[fill] {
    fill: var(--jp-inverse-layout-color3);
  }

  /* CSS for icons in status bar */
  #jp-main-statusbar .jp-mod-selected .jp-icon-selectable[fill] {
    fill: #fff;
  }

  #jp-main-statusbar .jp-mod-selected .jp-icon-selectable-inverse[fill] {
    fill: var(--jp-brand-color1);
  }
  /* special handling for splash icon CSS. While the theme CSS reloads during
    splash, the splash icon can loose theming. To prevent that, we set a
    default for its color variable */
  :root {
    --jp-warn-color0: var(--md-orange-700);
  }

  /* not sure what to do with this one, used in filebrowser listing */
  .jp-DragIcon {
    margin-right: 4px;
  }

  /*-----------------------------------------------------------------------------
  | Copyright (c) Jupyter Development Team.
  | Distributed under the terms of the Modified BSD License.
  |----------------------------------------------------------------------------*/

  /**
  * Support for alt colors for icons as inline SVG HTMLElements
  */

  /* alt recolor the primary elements of an icon */
  .jp-icon-alt .jp-icon0[fill] {
    fill: var(--jp-layout-color0);
  }
  .jp-icon-alt .jp-icon1[fill] {
    fill: var(--jp-layout-color1);
  }
  .jp-icon-alt .jp-icon2[fill] {
    fill: var(--jp-layout-color2);
  }
  .jp-icon-alt .jp-icon3[fill] {
    fill: var(--jp-layout-color3);
  }
  .jp-icon-alt .jp-icon4[fill] {
    fill: var(--jp-layout-color4);
  }

  .jp-icon-alt .jp-icon0[stroke] {
    stroke: var(--jp-layout-color0);
  }
  .jp-icon-alt .jp-icon1[stroke] {
    stroke: var(--jp-layout-color1);
  }
  .jp-icon-alt .jp-icon2[stroke] {
    stroke: var(--jp-layout-color2);
  }
  .jp-icon-alt .jp-icon3[stroke] {
    stroke: var(--jp-layout-color3);
  }
  .jp-icon-alt .jp-icon4[stroke] {
    stroke: var(--jp-layout-color4);
  }

  /* alt recolor the accent elements of an icon */
  .jp-icon-alt .jp-icon-accent0[fill] {
    fill: var(--jp-inverse-layout-color0);
  }
  .jp-icon-alt .jp-icon-accent1[fill] {
    fill: var(--jp-inverse-layout-color1);
  }
  .jp-icon-alt .jp-icon-accent2[fill] {
    fill: var(--jp-inverse-layout-color2);
  }
  .jp-icon-alt .jp-icon-accent3[fill] {
    fill: var(--jp-inverse-layout-color3);
  }
  .jp-icon-alt .jp-icon-accent4[fill] {
    fill: var(--jp-inverse-layout-color4);
  }

  .jp-icon-alt .jp-icon-accent0[stroke] {
    stroke: var(--jp-inverse-layout-color0);
  }
  .jp-icon-alt .jp-icon-accent1[stroke] {
    stroke: var(--jp-inverse-layout-color1);
  }
  .jp-icon-alt .jp-icon-accent2[stroke] {
    stroke: var(--jp-inverse-layout-color2);
  }
  .jp-icon-alt .jp-icon-accent3[stroke] {
    stroke: var(--jp-inverse-layout-color3);
  }
  .jp-icon-alt .jp-icon-accent4[stroke] {
    stroke: var(--jp-inverse-layout-color4);
  }

  /*-----------------------------------------------------------------------------
  | Copyright (c) Jupyter Development Team.
  | Distributed under the terms of the Modified BSD License.
  |----------------------------------------------------------------------------*/

  .jp-icon-hoverShow:not(:hover) svg {
    display: none !important;
  }

  /**
  * Support for hover colors for icons as inline SVG HTMLElements
  */

  /**
  * regular colors
  */

  /* recolor the primary elements of an icon */
  .jp-icon-hover :hover .jp-icon0-hover[fill] {
    fill: var(--jp-inverse-layout-color0);
  }
  .jp-icon-hover :hover .jp-icon1-hover[fill] {
    fill: var(--jp-inverse-layout-color1);
  }
  .jp-icon-hover :hover .jp-icon2-hover[fill] {
    fill: var(--jp-inverse-layout-color2);
  }
  .jp-icon-hover :hover .jp-icon3-hover[fill] {
    fill: var(--jp-inverse-layout-color3);
  }
  .jp-icon-hover :hover .jp-icon4-hover[fill] {
    fill: var(--jp-inverse-layout-color4);
  }

  .jp-icon-hover :hover .jp-icon0-hover[stroke] {
    stroke: var(--jp-inverse-layout-color0);
  }
  .jp-icon-hover :hover .jp-icon1-hover[stroke] {
    stroke: var(--jp-inverse-layout-color1);
  }
  .jp-icon-hover :hover .jp-icon2-hover[stroke] {
    stroke: var(--jp-inverse-layout-color2);
  }
  .jp-icon-hover :hover .jp-icon3-hover[stroke] {
    stroke: var(--jp-inverse-layout-color3);
  }
  .jp-icon-hover :hover .jp-icon4-hover[stroke] {
    stroke: var(--jp-inverse-layout-color4);
  }

  /* recolor the accent elements of an icon */
  .jp-icon-hover :hover .jp-icon-accent0-hover[fill] {
    fill: var(--jp-layout-color0);
  }
  .jp-icon-hover :hover .jp-icon-accent1-hover[fill] {
    fill: var(--jp-layout-color1);
  }
  .jp-icon-hover :hover .jp-icon-accent2-hover[fill] {
    fill: var(--jp-layout-color2);
  }
  .jp-icon-hover :hover .jp-icon-accent3-hover[fill] {
    fill: var(--jp-layout-color3);
  }
  .jp-icon-hover :hover .jp-icon-accent4-hover[fill] {
    fill: var(--jp-layout-color4);
  }

  .jp-icon-hover :hover .jp-icon-accent0-hover[stroke] {
    stroke: var(--jp-layout-color0);
  }
  .jp-icon-hover :hover .jp-icon-accent1-hover[stroke] {
    stroke: var(--jp-layout-color1);
  }
  .jp-icon-hover :hover .jp-icon-accent2-hover[stroke] {
    stroke: var(--jp-layout-color2);
  }
  .jp-icon-hover :hover .jp-icon-accent3-hover[stroke] {
    stroke: var(--jp-layout-color3);
  }
  .jp-icon-hover :hover .jp-icon-accent4-hover[stroke] {
    stroke: var(--jp-layout-color4);
  }

  /* set the color of an icon to transparent */
  .jp-icon-hover :hover .jp-icon-none-hover[fill] {
    fill: none;
  }

  .jp-icon-hover :hover .jp-icon-none-hover[stroke] {
    stroke: none;
  }

  /**
  * inverse colors
  */

  /* inverse recolor the primary elements of an icon */
  .jp-icon-hover.jp-icon-alt :hover .jp-icon0-hover[fill] {
    fill: var(--jp-layout-color0);
  }
  .jp-icon-hover.jp-icon-alt :hover .jp-icon1-hover[fill] {
    fill: var(--jp-layout-color1);
  }
  .jp-icon-hover.jp-icon-alt :hover .jp-icon2-hover[fill] {
    fill: var(--jp-layout-color2);
  }
  .jp-icon-hover.jp-icon-alt :hover .jp-icon3-hover[fill] {
    fill: var(--jp-layout-color3);
  }
  .jp-icon-hover.jp-icon-alt :hover .jp-icon4-hover[fill] {
    fill: var(--jp-layout-color4);
  }

  .jp-icon-hover.jp-icon-alt :hover .jp-icon0-hover[stroke] {
    stroke: var(--jp-layout-color0);
  }
  .jp-icon-hover.jp-icon-alt :hover .jp-icon1-hover[stroke] {
    stroke: var(--jp-layout-color1);
  }
  .jp-icon-hover.jp-icon-alt :hover .jp-icon2-hover[stroke] {
    stroke: var(--jp-layout-color2);
  }
  .jp-icon-hover.jp-icon-alt :hover .jp-icon3-hover[stroke] {
    stroke: var(--jp-layout-color3);
  }
  .jp-icon-hover.jp-icon-alt :hover .jp-icon4-hover[stroke] {
    stroke: var(--jp-layout-color4);
  }

  /* inverse recolor the accent elements of an icon */
  .jp-icon-hover.jp-icon-alt :hover .jp-icon-accent0-hover[fill] {
    fill: var(--jp-inverse-layout-color0);
  }
  .jp-icon-hover.jp-icon-alt :hover .jp-icon-accent1-hover[fill] {
    fill: var(--jp-inverse-layout-color1);
  }
  .jp-icon-hover.jp-icon-alt :hover .jp-icon-accent2-hover[fill] {
    fill: var(--jp-inverse-layout-color2);
  }
  .jp-icon-hover.jp-icon-alt :hover .jp-icon-accent3-hover[fill] {
    fill: var(--jp-inverse-layout-color3);
  }
  .jp-icon-hover.jp-icon-alt :hover .jp-icon-accent4-hover[fill] {
    fill: var(--jp-inverse-layout-color4);
  }

  .jp-icon-hover.jp-icon-alt :hover .jp-icon-accent0-hover[stroke] {
    stroke: var(--jp-inverse-layout-color0);
  }
  .jp-icon-hover.jp-icon-alt :hover .jp-icon-accent1-hover[stroke] {
    stroke: var(--jp-inverse-layout-color1);
  }
  .jp-icon-hover.jp-icon-alt :hover .jp-icon-accent2-hover[stroke] {
    stroke: var(--jp-inverse-layout-color2);
  }
  .jp-icon-hover.jp-icon-alt :hover .jp-icon-accent3-hover[stroke] {
    stroke: var(--jp-inverse-layout-color3);
  }
  .jp-icon-hover.jp-icon-alt :hover .jp-icon-accent4-hover[stroke] {
    stroke: var(--jp-inverse-layout-color4);
  }

  /*-----------------------------------------------------------------------------
  | Copyright (c) Jupyter Development Team.
  | Distributed under the terms of the Modified BSD License.
  |----------------------------------------------------------------------------*/

  .jp-switch {
    display: flex;
    align-items: center;
    padding-left: 4px;
    padding-right: 4px;
    font-size: var(--jp-ui-font-size1);
    background-color: transparent;
    color: var(--jp-ui-font-color1);
    border: none;
    height: 20px;
  }

  .jp-switch:hover {
    background-color: var(--jp-layout-color2);
  }

  .jp-switch-label {
    margin-right: 5px;
  }

  .jp-switch-track {
    cursor: pointer;
    background-color: var(--jp-border-color1);
    -webkit-transition: 0.4s;
    transition: 0.4s;
    border-radius: 34px;
    height: 16px;
    width: 35px;
    position: relative;
  }

  .jp-switch-track::before {
    content: '';
    position: absolute;
    height: 10px;
    width: 10px;
    margin: 3px;
    left: 0px;
    background-color: var(--jp-ui-inverse-font-color1);
    -webkit-transition: 0.4s;
    transition: 0.4s;
    border-radius: 50%;
  }

  .jp-switch[aria-checked='true'] .jp-switch-track {
    background-color: var(--jp-warn-color0);
  }

  .jp-switch[aria-checked='true'] .jp-switch-track::before {
    /* track width (35) - margins (3 + 3) - thumb width (10) */
    left: 19px;
  }

  /*-----------------------------------------------------------------------------
  | Copyright (c) Jupyter Development Team.
  | Distributed under the terms of the Modified BSD License.
  |----------------------------------------------------------------------------*/

  /* Sibling imports */

  /* Override Blueprint's _reset.scss styles */
  html {
    box-sizing: unset;
  }

  *,
  *::before,
  *::after {
    box-sizing: unset;
  }

  body {
    color: unset;
    font-family: var(--jp-ui-font-family);
  }

  p {
    margin-top: unset;
    margin-bottom: unset;
  }

  small {
    font-size: unset;
  }

  strong {
    font-weight: unset;
  }

  /* Override Blueprint's _typography.scss styles */
  a {
    text-decoration: unset;
    color: unset;
  }
  a:hover {
    text-decoration: unset;
    color: unset;
  }

  /* Override Blueprint's _accessibility.scss styles */
  :focus {
    outline: unset;
    outline-offset: unset;
    -moz-outline-radius: unset;
  }

  /* Styles for ui-components */
  .jp-Button {
    border-radius: var(--jp-border-radius);
    padding: 0px 12px;
    font-size: var(--jp-ui-font-size1);
  }

  /* Use our own theme for hover styles */
  button.jp-Button.bp3-button.bp3-minimal:hover {
    background-color: var(--jp-layout-color2);
  }
  .jp-Button.minimal {
    color: unset !important;
  }

  .jp-Button.jp-ToolbarButtonComponent {
    text-transform: none;
  }

  .jp-InputGroup input {
    box-sizing: border-box;
    border-radius: 0;
    background-color: transparent;
    color: var(--jp-ui-font-color0);
    box-shadow: inset 0 0 0 var(--jp-border-width) var(--jp-input-border-color);
  }

  .jp-InputGroup input:focus {
    box-shadow: inset 0 0 0 var(--jp-border-width)
        var(--jp-input-active-box-shadow-color),
      inset 0 0 0 3px var(--jp-input-active-box-shadow-color);
  }

  .jp-InputGroup input::placeholder,
  input::placeholder {
    color: var(--jp-ui-font-color3);
  }

  .jp-BPIcon {
    display: inline-block;
    vertical-align: middle;
    margin: auto;
  }

  /* Stop blueprint futzing with our icon fills */
  .bp3-icon.jp-BPIcon > svg:not([fill]) {
    fill: var(--jp-inverse-layout-color3);
  }

  .jp-InputGroupAction {
    padding: 6px;
  }

  .jp-HTMLSelect.jp-DefaultStyle select {
    background-color: initial;
    border: none;
    border-radius: 0;
    box-shadow: none;
    color: var(--jp-ui-font-color0);
    display: block;
    font-size: var(--jp-ui-font-size1);
    height: 24px;
    line-height: 14px;
    padding: 0 25px 0 10px;
    text-align: left;
    -moz-appearance: none;
    -webkit-appearance: none;
  }

  /* Use our own theme for hover and option styles */
  .jp-HTMLSelect.jp-DefaultStyle select:hover,
  .jp-HTMLSelect.jp-DefaultStyle select > option {
    background-color: var(--jp-layout-color2);
    color: var(--jp-ui-font-color0);
  }
  select {
    box-sizing: border-box;
  }

  /*-----------------------------------------------------------------------------
  | Copyright (c) Jupyter Development Team.
  | Distributed under the terms of the Modified BSD License.
  |----------------------------------------------------------------------------*/

  .jp-Collapse {
    display: flex;
    flex-direction: column;
    align-items: stretch;
    border-top: 1px solid var(--jp-border-color2);
    border-bottom: 1px solid var(--jp-border-color2);
  }

  .jp-Collapse-header {
    padding: 1px 12px;
    color: var(--jp-ui-font-color1);
    background-color: var(--jp-layout-color1);
    font-size: var(--jp-ui-font-size2);
  }

  .jp-Collapse-header:hover {
    background-color: var(--jp-layout-color2);
  }

  .jp-Collapse-contents {
    padding: 0px 12px 0px 12px;
    background-color: var(--jp-layout-color1);
    color: var(--jp-ui-font-color1);
    overflow: auto;
  }

  /*-----------------------------------------------------------------------------
  | Copyright (c) Jupyter Development Team.
  | Distributed under the terms of the Modified BSD License.
  |----------------------------------------------------------------------------*/

  /*-----------------------------------------------------------------------------
  | Variables
  |----------------------------------------------------------------------------*/

  :root {
    --jp-private-commandpalette-search-height: 28px;
  }

  /*-----------------------------------------------------------------------------
  | Overall styles
  |----------------------------------------------------------------------------*/

  .lm-CommandPalette {
    padding-bottom: 0px;
    color: var(--jp-ui-font-color1);
    background: var(--jp-layout-color1);
    /* This is needed so that all font sizing of children done in ems is
    * relative to this base size */
    font-size: var(--jp-ui-font-size1);
  }

  /*-----------------------------------------------------------------------------
  | Modal variant
  |----------------------------------------------------------------------------*/

  .jp-ModalCommandPalette {
    position: absolute;
    z-index: 10000;
    top: 38px;
    left: 30%;
    margin: 0;
    padding: 4px;
    width: 40%;
    box-shadow: var(--jp-elevation-z4);
    border-radius: 4px;
    background: var(--jp-layout-color0);
  }

  .jp-ModalCommandPalette .lm-CommandPalette {
    max-height: 40vh;
  }

  .jp-ModalCommandPalette .lm-CommandPalette .lm-close-icon::after {
    display: none;
  }

  .jp-ModalCommandPalette .lm-CommandPalette .lm-CommandPalette-header {
    display: none;
  }

  .jp-ModalCommandPalette .lm-CommandPalette .lm-CommandPalette-item {
    margin-left: 4px;
    margin-right: 4px;
  }

  .jp-ModalCommandPalette
    .lm-CommandPalette
    .lm-CommandPalette-item.lm-mod-disabled {
    display: none;
  }

  /*-----------------------------------------------------------------------------
  | Search
  |----------------------------------------------------------------------------*/

  .lm-CommandPalette-search {
    padding: 4px;
    background-color: var(--jp-layout-color1);
    z-index: 2;
  }

  .lm-CommandPalette-wrapper {
    overflow: overlay;
    padding: 0px 9px;
    background-color: var(--jp-input-active-background);
    height: 30px;
    box-shadow: inset 0 0 0 var(--jp-border-width) var(--jp-input-border-color);
  }

  .lm-CommandPalette.lm-mod-focused .lm-CommandPalette-wrapper {
    box-shadow: inset 0 0 0 1px var(--jp-input-active-box-shadow-color),
      inset 0 0 0 3px var(--jp-input-active-box-shadow-color);
  }

  .lm-CommandPalette-wrapper::after {
    content: ' ';
    color: white;
    background-color: var(--jp-brand-color1);
    position: absolute;
    top: 4px;
    right: 4px;
    height: 30px;
    width: 10px;
    padding: 0px 10px;
    background-image: var(--jp-icon-search-white);
    background-size: 20px;
    background-repeat: no-repeat;
    background-position: center;
  }

  .lm-CommandPalette-input {
    background: transparent;
    width: calc(100% - 18px);
    float: left;
    border: none;
    outline: none;
    font-size: var(--jp-ui-font-size1);
    color: var(--jp-ui-font-color0);
    line-height: var(--jp-private-commandpalette-search-height);
  }

  .lm-CommandPalette-input::-webkit-input-placeholder,
  .lm-CommandPalette-input::-moz-placeholder,
  .lm-CommandPalette-input:-ms-input-placeholder {
    color: var(--jp-ui-font-color3);
    font-size: var(--jp-ui-font-size1);
  }

  /*-----------------------------------------------------------------------------
  | Results
  |----------------------------------------------------------------------------*/

  .lm-CommandPalette-header:first-child {
    margin-top: 0px;
  }

  .lm-CommandPalette-header {
    border-bottom: solid var(--jp-border-width) var(--jp-border-color2);
    color: var(--jp-ui-font-color1);
    cursor: pointer;
    display: flex;
    font-size: var(--jp-ui-font-size0);
    font-weight: 600;
    letter-spacing: 1px;
    margin-top: 8px;
    padding: 8px 0 8px 12px;
    text-transform: uppercase;
  }

  .lm-CommandPalette-header.lm-mod-active {
    background: var(--jp-layout-color2);
  }

  .lm-CommandPalette-header > mark {
    background-color: transparent;
    font-weight: bold;
    color: var(--jp-ui-font-color1);
  }

  .lm-CommandPalette-item {
    padding: 4px 12px 4px 4px;
    color: var(--jp-ui-font-color1);
    font-size: var(--jp-ui-font-size1);
    font-weight: 400;
    display: flex;
  }

  .lm-CommandPalette-item.lm-mod-disabled {
    color: var(--jp-ui-font-color3);
  }

  .lm-CommandPalette-item.lm-mod-active {
    background: var(--jp-layout-color3);
  }

  .lm-CommandPalette-item.lm-mod-active:hover:not(.lm-mod-disabled) {
    background: var(--jp-layout-color4);
  }

  .lm-CommandPalette-item:hover:not(.lm-mod-active):not(.lm-mod-disabled) {
    background: var(--jp-layout-color2);
  }

  .lm-CommandPalette-itemContent {
    overflow: hidden;
  }

  .lm-CommandPalette-itemLabel > mark {
    color: var(--jp-ui-font-color0);
    background-color: transparent;
    font-weight: bold;
  }

  .lm-CommandPalette-item.lm-mod-disabled mark {
    color: var(--jp-ui-font-color3);
  }

  .lm-CommandPalette-item .lm-CommandPalette-itemIcon {
    margin: 0 4px 0 0;
    position: relative;
    width: 16px;
    top: 2px;
    flex: 0 0 auto;
  }

  .lm-CommandPalette-item.lm-mod-disabled .lm-CommandPalette-itemIcon {
    opacity: 0.4;
  }

  .lm-CommandPalette-item .lm-CommandPalette-itemShortcut {
    flex: 0 0 auto;
  }

  .lm-CommandPalette-itemCaption {
    display: none;
  }

  .lm-CommandPalette-content {
    background-color: var(--jp-layout-color1);
  }

  .lm-CommandPalette-content:empty:after {
    content: 'No results';
    margin: auto;
    margin-top: 20px;
    width: 100px;
    display: block;
    font-size: var(--jp-ui-font-size2);
    font-family: var(--jp-ui-font-family);
    font-weight: lighter;
  }

  .lm-CommandPalette-emptyMessage {
    text-align: center;
    margin-top: 24px;
    line-height: 1.32;
    padding: 0px 8px;
    color: var(--jp-content-font-color3);
  }

  /*-----------------------------------------------------------------------------
  | Copyright (c) 2014-2017, Jupyter Development Team.
  |
  | Distributed under the terms of the Modified BSD License.
  |----------------------------------------------------------------------------*/

  .jp-Dialog {
    position: absolute;
    z-index: 10000;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    top: 0px;
    left: 0px;
    margin: 0;
    padding: 0;
    width: 100%;
    height: 100%;
    background: var(--jp-dialog-background);
  }

  .jp-Dialog-content {
    display: flex;
    flex-direction: column;
    margin-left: auto;
    margin-right: auto;
    background: var(--jp-layout-color1);
    padding: 24px;
    padding-bottom: 12px;
    min-width: 300px;
    min-height: 150px;
    max-width: 1000px;
    max-height: 500px;
    box-sizing: border-box;
    box-shadow: var(--jp-elevation-z20);
    word-wrap: break-word;
    border-radius: var(--jp-border-radius);
    /* This is needed so that all font sizing of children done in ems is
    * relative to this base size */
    font-size: var(--jp-ui-font-size1);
    color: var(--jp-ui-font-color1);
    resize: both;
  }

  .jp-Dialog-button {
    overflow: visible;
  }

  button.jp-Dialog-button:focus {
    outline: 1px solid var(--jp-brand-color1);
    outline-offset: 4px;
    -moz-outline-radius: 0px;
  }

  button.jp-Dialog-button:focus::-moz-focus-inner {
    border: 0;
  }

  button.jp-Dialog-close-button {
    padding: 0;
    height: 100%;
    min-width: unset;
    min-height: unset;
  }

  .jp-Dialog-header {
    display: flex;
    justify-content: space-between;
    flex: 0 0 auto;
    padding-bottom: 12px;
    font-size: var(--jp-ui-font-size3);
    font-weight: 400;
    color: var(--jp-ui-font-color0);
  }

  .jp-Dialog-body {
    display: flex;
    flex-direction: column;
    flex: 1 1 auto;
    font-size: var(--jp-ui-font-size1);
    background: var(--jp-layout-color1);
    overflow: auto;
  }

  .jp-Dialog-footer {
    display: flex;
    flex-direction: row;
    justify-content: flex-end;
    flex: 0 0 auto;
    margin-left: -12px;
    margin-right: -12px;
    padding: 12px;
  }

  .jp-Dialog-title {
    overflow: hidden;
    white-space: nowrap;
    text-overflow: ellipsis;
  }

  .jp-Dialog-body > .jp-select-wrapper {
    width: 100%;
  }

  .jp-Dialog-body > button {
    padding: 0px 16px;
  }

  .jp-Dialog-body > label {
    line-height: 1.4;
    color: var(--jp-ui-font-color0);
  }

  .jp-Dialog-button.jp-mod-styled:not(:last-child) {
    margin-right: 12px;
  }

  /*-----------------------------------------------------------------------------
  | Copyright (c) 2014-2016, Jupyter Development Team.
  |
  | Distributed under the terms of the Modified BSD License.
  |----------------------------------------------------------------------------*/

  .jp-HoverBox {
    position: fixed;
  }

  .jp-HoverBox.jp-mod-outofview {
    display: none;
  }

  /*-----------------------------------------------------------------------------
  | Copyright (c) Jupyter Development Team.
  | Distributed under the terms of the Modified BSD License.
  |----------------------------------------------------------------------------*/

  .jp-IFrame {
    width: 100%;
    height: 100%;
  }

  .jp-IFrame > iframe {
    border: none;
  }

  /*
  When drag events occur, `p-mod-override-cursor` is added to the body.
  Because iframes steal all cursor events, the following two rules are necessary
  to suppress pointer events while resize drags are occurring. There may be a
  better solution to this problem.
  */
  body.lm-mod-override-cursor .jp-IFrame {
    position: relative;
  }

  body.lm-mod-override-cursor .jp-IFrame:before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: transparent;
  }

  /*-----------------------------------------------------------------------------
  | Copyright (c) 2014-2016, Jupyter Development Team.
  |
  | Distributed under the terms of the Modified BSD License.
  |----------------------------------------------------------------------------*/

  .jp-MainAreaWidget > :focus {
    outline: none;
  }

  /**
  * google-material-color v1.2.6
  * https://github.com/danlevan/google-material-color
  */
  :root {
    --md-red-50: #ffebee;
    --md-red-100: #ffcdd2;
    --md-red-200: #ef9a9a;
    --md-red-300: #e57373;
    --md-red-400: #ef5350;
    --md-red-500: #f44336;
    --md-red-600: #e53935;
    --md-red-700: #d32f2f;
    --md-red-800: #c62828;
    --md-red-900: #b71c1c;
    --md-red-A100: #ff8a80;
    --md-red-A200: #ff5252;
    --md-red-A400: #ff1744;
    --md-red-A700: #d50000;

    --md-pink-50: #fce4ec;
    --md-pink-100: #f8bbd0;
    --md-pink-200: #f48fb1;
    --md-pink-300: #f06292;
    --md-pink-400: #ec407a;
    --md-pink-500: #e91e63;
    --md-pink-600: #d81b60;
    --md-pink-700: #c2185b;
    --md-pink-800: #ad1457;
    --md-pink-900: #880e4f;
    --md-pink-A100: #ff80ab;
    --md-pink-A200: #ff4081;
    --md-pink-A400: #f50057;
    --md-pink-A700: #c51162;

    --md-purple-50: #f3e5f5;
    --md-purple-100: #e1bee7;
    --md-purple-200: #ce93d8;
    --md-purple-300: #ba68c8;
    --md-purple-400: #ab47bc;
    --md-purple-500: #9c27b0;
    --md-purple-600: #8e24aa;
    --md-purple-700: #7b1fa2;
    --md-purple-800: #6a1b9a;
    --md-purple-900: #4a148c;
    --md-purple-A100: #ea80fc;
    --md-purple-A200: #e040fb;
    --md-purple-A400: #d500f9;
    --md-purple-A700: #aa00ff;

    --md-deep-purple-50: #ede7f6;
    --md-deep-purple-100: #d1c4e9;
    --md-deep-purple-200: #b39ddb;
    --md-deep-purple-300: #9575cd;
    --md-deep-purple-400: #7e57c2;
    --md-deep-purple-500: #673ab7;
    --md-deep-purple-600: #5e35b1;
    --md-deep-purple-700: #512da8;
    --md-deep-purple-800: #4527a0;
    --md-deep-purple-900: #311b92;
    --md-deep-purple-A100: #b388ff;
    --md-deep-purple-A200: #7c4dff;
    --md-deep-purple-A400: #651fff;
    --md-deep-purple-A700: #6200ea;

    --md-indigo-50: #e8eaf6;
    --md-indigo-100: #c5cae9;
    --md-indigo-200: #9fa8da;
    --md-indigo-300: #7986cb;
    --md-indigo-400: #5c6bc0;
    --md-indigo-500: #3f51b5;
    --md-indigo-600: #3949ab;
    --md-indigo-700: #303f9f;
    --md-indigo-800: #283593;
    --md-indigo-900: #1a237e;
    --md-indigo-A100: #8c9eff;
    --md-indigo-A200: #536dfe;
    --md-indigo-A400: #3d5afe;
    --md-indigo-A700: #304ffe;

    --md-blue-50: #e3f2fd;
    --md-blue-100: #bbdefb;
    --md-blue-200: #90caf9;
    --md-blue-300: #64b5f6;
    --md-blue-400: #42a5f5;
    --md-blue-500: #2196f3;
    --md-blue-600: #1e88e5;
    --md-blue-700: #1976d2;
    --md-blue-800: #1565c0;
    --md-blue-900: #0d47a1;
    --md-blue-A100: #82b1ff;
    --md-blue-A200: #448aff;
    --md-blue-A400: #2979ff;
    --md-blue-A700: #2962ff;

    --md-light-blue-50: #e1f5fe;
    --md-light-blue-100: #b3e5fc;
    --md-light-blue-200: #81d4fa;
    --md-light-blue-300: #4fc3f7;
    --md-light-blue-400: #29b6f6;
    --md-light-blue-500: #03a9f4;
    --md-light-blue-600: #039be5;
    --md-light-blue-700: #0288d1;
    --md-light-blue-800: #0277bd;
    --md-light-blue-900: #01579b;
    --md-light-blue-A100: #80d8ff;
    --md-light-blue-A200: #40c4ff;
    --md-light-blue-A400: #00b0ff;
    --md-light-blue-A700: #0091ea;

    --md-cyan-50: #e0f7fa;
    --md-cyan-100: #b2ebf2;
    --md-cyan-200: #80deea;
    --md-cyan-300: #4dd0e1;
    --md-cyan-400: #26c6da;
    --md-cyan-500: #00bcd4;
    --md-cyan-600: #00acc1;
    --md-cyan-700: #0097a7;
    --md-cyan-800: #00838f;
    --md-cyan-900: #006064;
    --md-cyan-A100: #84ffff;
    --md-cyan-A200: #18ffff;
    --md-cyan-A400: #00e5ff;
    --md-cyan-A700: #00b8d4;

    --md-teal-50: #e0f2f1;
    --md-teal-100: #b2dfdb;
    --md-teal-200: #80cbc4;
    --md-teal-300: #4db6ac;
    --md-teal-400: #26a69a;
    --md-teal-500: #009688;
    --md-teal-600: #00897b;
    --md-teal-700: #00796b;
    --md-teal-800: #00695c;
    --md-teal-900: #004d40;
    --md-teal-A100: #a7ffeb;
    --md-teal-A200: #64ffda;
    --md-teal-A400: #1de9b6;
    --md-teal-A700: #00bfa5;

    --md-green-50: #e8f5e9;
    --md-green-100: #c8e6c9;
    --md-green-200: #a5d6a7;
    --md-green-300: #81c784;
    --md-green-400: #66bb6a;
    --md-green-500: #4caf50;
    --md-green-600: #43a047;
    --md-green-700: #388e3c;
    --md-green-800: #2e7d32;
    --md-green-900: #1b5e20;
    --md-green-A100: #b9f6ca;
    --md-green-A200: #69f0ae;
    --md-green-A400: #00e676;
    --md-green-A700: #00c853;

    --md-light-green-50: #f1f8e9;
    --md-light-green-100: #dcedc8;
    --md-light-green-200: #c5e1a5;
    --md-light-green-300: #aed581;
    --md-light-green-400: #9ccc65;
    --md-light-green-500: #8bc34a;
    --md-light-green-600: #7cb342;
    --md-light-green-700: #689f38;
    --md-light-green-800: #558b2f;
    --md-light-green-900: #33691e;
    --md-light-green-A100: #ccff90;
    --md-light-green-A200: #b2ff59;
    --md-light-green-A400: #76ff03;
    --md-light-green-A700: #64dd17;

    --md-lime-50: #f9fbe7;
    --md-lime-100: #f0f4c3;
    --md-lime-200: #e6ee9c;
    --md-lime-300: #dce775;
    --md-lime-400: #d4e157;
    --md-lime-500: #cddc39;
    --md-lime-600: #c0ca33;
    --md-lime-700: #afb42b;
    --md-lime-800: #9e9d24;
    --md-lime-900: #827717;
    --md-lime-A100: #f4ff81;
    --md-lime-A200: #eeff41;
    --md-lime-A400: #c6ff00;
    --md-lime-A700: #aeea00;

    --md-yellow-50: #fffde7;
    --md-yellow-100: #fff9c4;
    --md-yellow-200: #fff59d;
    --md-yellow-300: #fff176;
    --md-yellow-400: #ffee58;
    --md-yellow-500: #ffeb3b;
    --md-yellow-600: #fdd835;
    --md-yellow-700: #fbc02d;
    --md-yellow-800: #f9a825;
    --md-yellow-900: #f57f17;
    --md-yellow-A100: #ffff8d;
    --md-yellow-A200: #ffff00;
    --md-yellow-A400: #ffea00;
    --md-yellow-A700: #ffd600;

    --md-amber-50: #fff8e1;
    --md-amber-100: #ffecb3;
    --md-amber-200: #ffe082;
    --md-amber-300: #ffd54f;
    --md-amber-400: #ffca28;
    --md-amber-500: #ffc107;
    --md-amber-600: #ffb300;
    --md-amber-700: #ffa000;
    --md-amber-800: #ff8f00;
    --md-amber-900: #ff6f00;
    --md-amber-A100: #ffe57f;
    --md-amber-A200: #ffd740;
    --md-amber-A400: #ffc400;
    --md-amber-A700: #ffab00;

    --md-orange-50: #fff3e0;
    --md-orange-100: #ffe0b2;
    --md-orange-200: #ffcc80;
    --md-orange-300: #ffb74d;
    --md-orange-400: #ffa726;
    --md-orange-500: #ff9800;
    --md-orange-600: #fb8c00;
    --md-orange-700: #f57c00;
    --md-orange-800: #ef6c00;
    --md-orange-900: #e65100;
    --md-orange-A100: #ffd180;
    --md-orange-A200: #ffab40;
    --md-orange-A400: #ff9100;
    --md-orange-A700: #ff6d00;

    --md-deep-orange-50: #fbe9e7;
    --md-deep-orange-100: #ffccbc;
    --md-deep-orange-200: #ffab91;
    --md-deep-orange-300: #ff8a65;
    --md-deep-orange-400: #ff7043;
    --md-deep-orange-500: #ff5722;
    --md-deep-orange-600: #f4511e;
    --md-deep-orange-700: #e64a19;
    --md-deep-orange-800: #d84315;
    --md-deep-orange-900: #bf360c;
    --md-deep-orange-A100: #ff9e80;
    --md-deep-orange-A200: #ff6e40;
    --md-deep-orange-A400: #ff3d00;
    --md-deep-orange-A700: #dd2c00;

    --md-brown-50: #efebe9;
    --md-brown-100: #d7ccc8;
    --md-brown-200: #bcaaa4;
    --md-brown-300: #a1887f;
    --md-brown-400: #8d6e63;
    --md-brown-500: #795548;
    --md-brown-600: #6d4c41;
    --md-brown-700: #5d4037;
    --md-brown-800: #4e342e;
    --md-brown-900: #3e2723;

    --md-grey-50: #fafafa;
    --md-grey-100: #f5f5f5;
    --md-grey-200: #eeeeee;
    --md-grey-300: #e0e0e0;
    --md-grey-400: #bdbdbd;
    --md-grey-500: #9e9e9e;
    --md-grey-600: #757575;
    --md-grey-700: #616161;
    --md-grey-800: #424242;
    --md-grey-900: #212121;

    --md-blue-grey-50: #eceff1;
    --md-blue-grey-100: #cfd8dc;
    --md-blue-grey-200: #b0bec5;
    --md-blue-grey-300: #90a4ae;
    --md-blue-grey-400: #78909c;
    --md-blue-grey-500: #607d8b;
    --md-blue-grey-600: #546e7a;
    --md-blue-grey-700: #455a64;
    --md-blue-grey-800: #37474f;
    --md-blue-grey-900: #263238;
  }

  /*-----------------------------------------------------------------------------
  | Copyright (c) 2017, Jupyter Development Team.
  |
  | Distributed under the terms of the Modified BSD License.
  |----------------------------------------------------------------------------*/

  .jp-Spinner {
    position: absolute;
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 10;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    background: var(--jp-layout-color0);
    outline: none;
  }

  .jp-SpinnerContent {
    font-size: 10px;
    margin: 50px auto;
    text-indent: -9999em;
    width: 3em;
    height: 3em;
    border-radius: 50%;
    background: var(--jp-brand-color3);
    background: linear-gradient(
      to right,
      #f37626 10%,
      rgba(255, 255, 255, 0) 42%
    );
    position: relative;
    animation: load3 1s infinite linear, fadeIn 1s;
  }

  .jp-SpinnerContent:before {
    width: 50%;
    height: 50%;
    background: #f37626;
    border-radius: 100% 0 0 0;
    position: absolute;
    top: 0;
    left: 0;
    content: '';
  }

  .jp-SpinnerContent:after {
    background: var(--jp-layout-color0);
    width: 75%;
    height: 75%;
    border-radius: 50%;
    content: '';
    margin: auto;
    position: absolute;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
  }

  @keyframes fadeIn {
    0% {
      opacity: 0;
    }
    100% {
      opacity: 1;
    }
  }

  @keyframes load3 {
    0% {
      transform: rotate(0deg);
    }
    100% {
      transform: rotate(360deg);
    }
  }

  /*-----------------------------------------------------------------------------
  | Copyright (c) 2014-2017, Jupyter Development Team.
  |
  | Distributed under the terms of the Modified BSD License.
  |----------------------------------------------------------------------------*/

  button.jp-mod-styled {
    font-size: var(--jp-ui-font-size1);
    color: var(--jp-ui-font-color0);
    border: none;
    box-sizing: border-box;
    text-align: center;
    line-height: 32px;
    height: 32px;
    padding: 0px 12px;
    letter-spacing: 0.8px;
    outline: none;
    appearance: none;
    -webkit-appearance: none;
    -moz-appearance: none;
  }

  input.jp-mod-styled {
    background: var(--jp-input-background);
    height: 28px;
    box-sizing: border-box;
    border: var(--jp-border-width) solid var(--jp-border-color1);
    padding-left: 7px;
    padding-right: 7px;
    font-size: var(--jp-ui-font-size2);
    color: var(--jp-ui-font-color0);
    outline: none;
    appearance: none;
    -webkit-appearance: none;
    -moz-appearance: none;
  }

  input.jp-mod-styled:focus {
    border: var(--jp-border-width) solid var(--md-blue-500);
    box-shadow: inset 0 0 4px var(--md-blue-300);
  }

  .jp-select-wrapper {
    display: flex;
    position: relative;
    flex-direction: column;
    padding: 1px;
    background-color: var(--jp-layout-color1);
    height: 28px;
    box-sizing: border-box;
    margin-bottom: 12px;
  }

  .jp-select-wrapper.jp-mod-focused select.jp-mod-styled {
    border: var(--jp-border-width) solid var(--jp-input-active-border-color);
    box-shadow: var(--jp-input-box-shadow);
    background-color: var(--jp-input-active-background);
  }

  select.jp-mod-styled:hover {
    background-color: var(--jp-layout-color1);
    cursor: pointer;
    color: var(--jp-ui-font-color0);
    background-color: var(--jp-input-hover-background);
    box-shadow: inset 0 0px 1px rgba(0, 0, 0, 0.5);
  }

  select.jp-mod-styled {
    flex: 1 1 auto;
    height: 32px;
    width: 100%;
    font-size: var(--jp-ui-font-size2);
    background: var(--jp-input-background);
    color: var(--jp-ui-font-color0);
    padding: 0 25px 0 8px;
    border: var(--jp-border-width) solid var(--jp-input-border-color);
    border-radius: 0px;
    outline: none;
    appearance: none;
    -webkit-appearance: none;
    -moz-appearance: none;
  }

  /*-----------------------------------------------------------------------------
  | Copyright (c) 2014-2016, Jupyter Development Team.
  |
  | Distributed under the terms of the Modified BSD License.
  |----------------------------------------------------------------------------*/

  :root {
    --jp-private-toolbar-height: calc(
      28px + var(--jp-border-width)
    ); /* leave 28px for content */
  }

  .jp-Toolbar {
    color: var(--jp-ui-font-color1);
    flex: 0 0 auto;
    display: flex;
    flex-direction: row;
    border-bottom: var(--jp-border-width) solid var(--jp-toolbar-border-color);
    box-shadow: var(--jp-toolbar-box-shadow);
    background: var(--jp-toolbar-background);
    min-height: var(--jp-toolbar-micro-height);
    padding: 2px;
    z-index: 1;
    overflow-x: hidden;
  }

  .jp-Toolbar:hover {
    overflow-x: auto;
  }

  /* Toolbar items */

  .jp-Toolbar > .jp-Toolbar-item.jp-Toolbar-spacer {
    flex-grow: 1;
    flex-shrink: 1;
  }

  .jp-Toolbar-item.jp-Toolbar-kernelStatus {
    display: inline-block;
    width: 32px;
    background-repeat: no-repeat;
    background-position: center;
    background-size: 16px;
  }

  .jp-Toolbar > .jp-Toolbar-item {
    flex: 0 0 auto;
    display: flex;
    padding-left: 1px;
    padding-right: 1px;
    font-size: var(--jp-ui-font-size1);
    line-height: var(--jp-private-toolbar-height);
    height: 100%;
  }

  /* Toolbar buttons */

  /* This is the div we use to wrap the react component into a Widget */
  div.jp-ToolbarButton {
    color: transparent;
    border: none;
    box-sizing: border-box;
    outline: none;
    appearance: none;
    -webkit-appearance: none;
    -moz-appearance: none;
    padding: 0px;
    margin: 0px;
  }

  button.jp-ToolbarButtonComponent {
    background: var(--jp-layout-color1);
    border: none;
    box-sizing: border-box;
    outline: none;
    appearance: none;
    -webkit-appearance: none;
    -moz-appearance: none;
    padding: 0px 6px;
    margin: 0px;
    height: 24px;
    border-radius: var(--jp-border-radius);
    display: flex;
    align-items: center;
    text-align: center;
    font-size: 14px;
    min-width: unset;
    min-height: unset;
  }

  button.jp-ToolbarButtonComponent:disabled {
    opacity: 0.4;
  }

  button.jp-ToolbarButtonComponent span {
    padding: 0px;
    flex: 0 0 auto;
  }

  button.jp-ToolbarButtonComponent .jp-ToolbarButtonComponent-label {
    font-size: var(--jp-ui-font-size1);
    line-height: 100%;
    padding-left: 2px;
    color: var(--jp-ui-font-color1);
  }

  #jp-main-dock-panel[data-mode='single-document']
    .jp-MainAreaWidget
    > .jp-Toolbar.jp-Toolbar-micro {
    padding: 0;
    min-height: 0;
  }

  #jp-main-dock-panel[data-mode='single-document']
    .jp-MainAreaWidget
    > .jp-Toolbar {
    border: none;
    box-shadow: none;
  }

  /*-----------------------------------------------------------------------------
  | Copyright (c) 2014-2017, Jupyter Development Team.
  |
  | Distributed under the terms of the Modified BSD License.
  |----------------------------------------------------------------------------*/

  /*-----------------------------------------------------------------------------
  | Copyright (c) Jupyter Development Team.
  | Copyright (c) 2014-2017, PhosphorJS Contributors
  |
  | Distributed under the terms of the BSD 3-Clause License.
  |
  | The full license is in the file LICENSE, distributed with this software.
  |----------------------------------------------------------------------------*/


  /* <DEPRECATED> */ body.p-mod-override-cursor *, /* </DEPRECATED> */
  body.lm-mod-override-cursor * {
    cursor: inherit !important;
  }

  /*-----------------------------------------------------------------------------
  | Copyright (c) 2014-2016, Jupyter Development Team.
  |
  | Distributed under the terms of the Modified BSD License.
  |----------------------------------------------------------------------------*/

  .jp-JSONEditor {
    display: flex;
    flex-direction: column;
    width: 100%;
  }

  .jp-JSONEditor-host {
    flex: 1 1 auto;
    border: var(--jp-border-width) solid var(--jp-input-border-color);
    border-radius: 0px;
    background: var(--jp-layout-color0);
    min-height: 50px;
    padding: 1px;
  }

  .jp-JSONEditor.jp-mod-error .jp-JSONEditor-host {
    border-color: red;
    outline-color: red;
  }

  .jp-JSONEditor-header {
    display: flex;
    flex: 1 0 auto;
    padding: 0 0 0 12px;
  }

  .jp-JSONEditor-header label {
    flex: 0 0 auto;
  }

  .jp-JSONEditor-commitButton {
    height: 16px;
    width: 16px;
    background-size: 18px;
    background-repeat: no-repeat;
    background-position: center;
  }

  .jp-JSONEditor-host.jp-mod-focused {
    background-color: var(--jp-input-active-background);
    border: 1px solid var(--jp-input-active-border-color);
    box-shadow: var(--jp-input-box-shadow);
  }

  .jp-Editor.jp-mod-dropTarget {
    border: var(--jp-border-width) solid var(--jp-input-active-border-color);
    box-shadow: var(--jp-input-box-shadow);
  }

  /* BASICS */

  .CodeMirror {
    /* Set height, width, borders, and global font properties here */
    font-family: monospace;
    height: 300px;
    color: black;
    direction: ltr;
  }

  /* PADDING */

  .CodeMirror-lines {
    padding: 4px 0; /* Vertical padding around content */
  }
  .CodeMirror pre.CodeMirror-line,
  .CodeMirror pre.CodeMirror-line-like {
    padding: 0 4px; /* Horizontal padding of content */
  }

  .CodeMirror-scrollbar-filler, .CodeMirror-gutter-filler {
    background-color: white; /* The little square between H and V scrollbars */
  }

  /* GUTTER */

  .CodeMirror-gutters {
    border-right: 1px solid #ddd;
    background-color: #f7f7f7;
    white-space: nowrap;
  }
  .CodeMirror-linenumbers {}
  .CodeMirror-linenumber {
    padding: 0 3px 0 5px;
    min-width: 20px;
    text-align: right;
    color: #999;
    white-space: nowrap;
  }

  .CodeMirror-guttermarker { color: black; }
  .CodeMirror-guttermarker-subtle { color: #999; }

  /* CURSOR */

  .CodeMirror-cursor {
    border-left: 1px solid black;
    border-right: none;
    width: 0;
  }
  /* Shown when moving in bi-directional text */
  .CodeMirror div.CodeMirror-secondarycursor {
    border-left: 1px solid silver;
  }
  .cm-fat-cursor .CodeMirror-cursor {
    width: auto;
    border: 0 !important;
    background: #7e7;
  }
  .cm-fat-cursor div.CodeMirror-cursors {
    z-index: 1;
  }
  .cm-fat-cursor-mark {
    background-color: rgba(20, 255, 20, 0.5);
    -webkit-animation: blink 1.06s steps(1) infinite;
    -moz-animation: blink 1.06s steps(1) infinite;
    animation: blink 1.06s steps(1) infinite;
  }
  .cm-animate-fat-cursor {
    width: auto;
    border: 0;
    -webkit-animation: blink 1.06s steps(1) infinite;
    -moz-animation: blink 1.06s steps(1) infinite;
    animation: blink 1.06s steps(1) infinite;
    background-color: #7e7;
  }
  @-moz-keyframes blink {
    0% {}
    50% { background-color: transparent; }
    100% {}
  }
  @-webkit-keyframes blink {
    0% {}
    50% { background-color: transparent; }
    100% {}
  }
  @keyframes blink {
    0% {}
    50% { background-color: transparent; }
    100% {}
  }

  /* Can style cursor different in overwrite (non-insert) mode */
  .CodeMirror-overwrite .CodeMirror-cursor {}

  .cm-tab { display: inline-block; text-decoration: inherit; }

  .CodeMirror-rulers {
    position: absolute;
    left: 0; right: 0; top: -50px; bottom: 0;
    overflow: hidden;
  }
  .CodeMirror-ruler {
    border-left: 1px solid #ccc;
    top: 0; bottom: 0;
    position: absolute;
  }

  /* DEFAULT THEME */

  .cm-s-default .cm-header {color: blue;}
  .cm-s-default .cm-quote {color: #090;}
  .cm-negative {color: #d44;}
  .cm-positive {color: #292;}
  .cm-header, .cm-strong {font-weight: bold;}
  .cm-em {font-style: italic;}
  .cm-link {text-decoration: underline;}
  .cm-strikethrough {text-decoration: line-through;}

  .cm-s-default .cm-keyword {color: #708;}
  .cm-s-default .cm-atom {color: #219;}
  .cm-s-default .cm-number {color: #164;}
  .cm-s-default .cm-def {color: #00f;}
  .cm-s-default .cm-variable,
  .cm-s-default .cm-punctuation,
  .cm-s-default .cm-property,
  .cm-s-default .cm-operator {}
  .cm-s-default .cm-variable-2 {color: #05a;}
  .cm-s-default .cm-variable-3, .cm-s-default .cm-type {color: #085;}
  .cm-s-default .cm-comment {color: #a50;}
  .cm-s-default .cm-string {color: #a11;}
  .cm-s-default .cm-string-2 {color: #f50;}
  .cm-s-default .cm-meta {color: #555;}
  .cm-s-default .cm-qualifier {color: #555;}
  .cm-s-default .cm-builtin {color: #30a;}
  .cm-s-default .cm-bracket {color: #997;}
  .cm-s-default .cm-tag {color: #170;}
  .cm-s-default .cm-attribute {color: #00c;}
  .cm-s-default .cm-hr {color: #999;}
  .cm-s-default .cm-link {color: #00c;}

  .cm-s-default .cm-error {color: #f00;}
  .cm-invalidchar {color: #f00;}

  .CodeMirror-composing { border-bottom: 2px solid; }

  /* Default styles for common addons */

  div.CodeMirror span.CodeMirror-matchingbracket {color: #0b0;}
  div.CodeMirror span.CodeMirror-nonmatchingbracket {color: #a22;}
  .CodeMirror-matchingtag { background: rgba(255, 150, 0, .3); }
  .CodeMirror-activeline-background {background: #e8f2ff;}

  /* STOP */

  /* The rest of this file contains styles related to the mechanics of
    the editor. You probably shouldn't touch them. */

  .CodeMirror {
    position: relative;
    overflow: hidden;
    background: white;
  }

  .CodeMirror-scroll {
    overflow: scroll !important; /* Things will break if this is overridden */
    /* 50px is the magic margin used to hide the element's real scrollbars */
    /* See overflow: hidden in .CodeMirror */
    margin-bottom: -50px; margin-right: -50px;
    padding-bottom: 50px;
    height: 100%;
    outline: none; /* Prevent dragging from highlighting the element */
    position: relative;
  }
  .CodeMirror-sizer {
    position: relative;
    border-right: 50px solid transparent;
  }

  /* The fake, visible scrollbars. Used to force redraw during scrolling
    before actual scrolling happens, thus preventing shaking and
    flickering artifacts. */
  .CodeMirror-vscrollbar, .CodeMirror-hscrollbar, .CodeMirror-scrollbar-filler, .CodeMirror-gutter-filler {
    position: absolute;
    z-index: 6;
    display: none;
  }
  .CodeMirror-vscrollbar {
    right: 0; top: 0;
    overflow-x: hidden;
    overflow-y: scroll;
  }
  .CodeMirror-hscrollbar {
    bottom: 0; left: 0;
    overflow-y: hidden;
    overflow-x: scroll;
  }
  .CodeMirror-scrollbar-filler {
    right: 0; bottom: 0;
  }
  .CodeMirror-gutter-filler {
    left: 0; bottom: 0;
  }

  .CodeMirror-gutters {
    position: absolute; left: 0; top: 0;
    min-height: 100%;
    z-index: 3;
  }
  .CodeMirror-gutter {
    white-space: normal;
    height: 100%;
    display: inline-block;
    vertical-align: top;
    margin-bottom: -50px;
  }
  .CodeMirror-gutter-wrapper {
    position: absolute;
    z-index: 4;
    background: none !important;
    border: none !important;
  }
  .CodeMirror-gutter-background {
    position: absolute;
    top: 0; bottom: 0;
    z-index: 4;
  }
  .CodeMirror-gutter-elt {
    position: absolute;
    cursor: default;
    z-index: 4;
  }
  .CodeMirror-gutter-wrapper ::selection { background-color: transparent }
  .CodeMirror-gutter-wrapper ::-moz-selection { background-color: transparent }

  .CodeMirror-lines {
    cursor: text;
    min-height: 1px; /* prevents collapsing before first draw */
  }
  .CodeMirror pre.CodeMirror-line,
  .CodeMirror pre.CodeMirror-line-like {
    /* Reset some styles that the rest of the page might have set */
    -moz-border-radius: 0; -webkit-border-radius: 0; border-radius: 0;
    border-width: 0;
    background: transparent;
    font-family: inherit;
    font-size: inherit;
    margin: 0;
    white-space: pre;
    word-wrap: normal;
    line-height: inherit;
    color: inherit;
    z-index: 2;
    position: relative;
    overflow: visible;
    -webkit-tap-highlight-color: transparent;
    -webkit-font-variant-ligatures: contextual;
    font-variant-ligatures: contextual;
  }
  .CodeMirror-wrap pre.CodeMirror-line,
  .CodeMirror-wrap pre.CodeMirror-line-like {
    word-wrap: break-word;
    white-space: pre-wrap;
    word-break: normal;
  }

  .CodeMirror-linebackground {
    position: absolute;
    left: 0; right: 0; top: 0; bottom: 0;
    z-index: 0;
  }

  .CodeMirror-linewidget {
    position: relative;
    z-index: 2;
    padding: 0.1px; /* Force widget margins to stay inside of the container */
  }

  .CodeMirror-widget {}

  .CodeMirror-rtl pre { direction: rtl; }

  .CodeMirror-code {
    outline: none;
  }

  /* Force content-box sizing for the elements where we expect it */
  .CodeMirror-scroll,
  .CodeMirror-sizer,
  .CodeMirror-gutter,
  .CodeMirror-gutters,
  .CodeMirror-linenumber {
    -moz-box-sizing: content-box;
    box-sizing: content-box;
  }

  .CodeMirror-measure {
    position: absolute;
    width: 100%;
    height: 0;
    overflow: hidden;
    visibility: hidden;
  }

  .CodeMirror-cursor {
    position: absolute;
    pointer-events: none;
  }
  .CodeMirror-measure pre { position: static; }

  div.CodeMirror-cursors {
    visibility: hidden;
    position: relative;
    z-index: 3;
  }
  div.CodeMirror-dragcursors {
    visibility: visible;
  }

  .CodeMirror-focused div.CodeMirror-cursors {
    visibility: visible;
  }

  .CodeMirror-selected { background: #d9d9d9; }
  .CodeMirror-focused .CodeMirror-selected { background: #d7d4f0; }
  .CodeMirror-crosshair { cursor: crosshair; }
  .CodeMirror-line::selection, .CodeMirror-line > span::selection, .CodeMirror-line > span > span::selection { background: #d7d4f0; }
  .CodeMirror-line::-moz-selection, .CodeMirror-line > span::-moz-selection, .CodeMirror-line > span > span::-moz-selection { background: #d7d4f0; }

  .cm-searching {
    background-color: #ffa;
    background-color: rgba(255, 255, 0, .4);
  }

  /* Used to force a border model for a node */
  .cm-force-border { padding-right: .1px; }

  @media print {
    /* Hide the cursor when printing */
    .CodeMirror div.CodeMirror-cursors {
      visibility: hidden;
    }
  }

  /* See issue #2901 */
  .cm-tab-wrap-hack:after { content: ''; }

  /* Help users use markselection to safely style text background */
  span.CodeMirror-selectedtext { background: none; }

  .CodeMirror-dialog {
    position: absolute;
    left: 0; right: 0;
    background: inherit;
    z-index: 15;
    padding: .1em .8em;
    overflow: hidden;
    color: inherit;
  }

  .CodeMirror-dialog-top {
    border-bottom: 1px solid #eee;
    top: 0;
  }

  .CodeMirror-dialog-bottom {
    border-top: 1px solid #eee;
    bottom: 0;
  }

  .CodeMirror-dialog input {
    border: none;
    outline: none;
    background: transparent;
    width: 20em;
    color: inherit;
    font-family: monospace;
  }

  .CodeMirror-dialog button {
    font-size: 70%;
  }

  .CodeMirror-foldmarker {
    color: blue;
    text-shadow: #b9f 1px 1px 2px, #b9f -1px -1px 2px, #b9f 1px -1px 2px, #b9f -1px 1px 2px;
    font-family: arial;
    line-height: .3;
    cursor: pointer;
  }
  .CodeMirror-foldgutter {
    width: .7em;
  }
  .CodeMirror-foldgutter-open,
  .CodeMirror-foldgutter-folded {
    cursor: pointer;
  }
  .CodeMirror-foldgutter-open:after {
    content: "\25BE";
  }
  .CodeMirror-foldgutter-folded:after {
    content: "\25B8";
  }

  /*-----------------------------------------------------------------------------
  | Copyright (c) Jupyter Development Team.
  | Distributed under the terms of the Modified BSD License.
  |----------------------------------------------------------------------------*/

  .CodeMirror {
    line-height: var(--jp-code-line-height);
    font-size: var(--jp-code-font-size);
    font-family: var(--jp-code-font-family);
    border: 0;
    border-radius: 0;
    height: auto;
    /* Changed to auto to autogrow */
  }

  .CodeMirror pre {
    padding: 0 var(--jp-code-padding);
  }

  .jp-CodeMirrorEditor[data-type='inline'] .CodeMirror-dialog {
    background-color: var(--jp-layout-color0);
    color: var(--jp-content-font-color1);
  }

  /* This causes https://github.com/jupyter/jupyterlab/issues/522 */
  /* May not cause it not because we changed it! */
  .CodeMirror-lines {
    padding: var(--jp-code-padding) 0;
  }

  .CodeMirror-linenumber {
    padding: 0 8px;
  }

  .jp-CodeMirrorEditor {
    cursor: text;
  }

  .jp-CodeMirrorEditor[data-type='inline'] .CodeMirror-cursor {
    border-left: var(--jp-code-cursor-width0) solid var(--jp-editor-cursor-color);
  }

  /* When zoomed out 67% and 33% on a screen of 1440 width x 900 height */
  @media screen and (min-width: 2138px) and (max-width: 4319px) {
    .jp-CodeMirrorEditor[data-type='inline'] .CodeMirror-cursor {
      border-left: var(--jp-code-cursor-width1) solid
        var(--jp-editor-cursor-color);
    }
  }

  /* When zoomed out less than 33% */
  @media screen and (min-width: 4320px) {
    .jp-CodeMirrorEditor[data-type='inline'] .CodeMirror-cursor {
      border-left: var(--jp-code-cursor-width2) solid
        var(--jp-editor-cursor-color);
    }
  }

  .CodeMirror.jp-mod-readOnly .CodeMirror-cursor {
    display: none;
  }

  .CodeMirror-gutters {
    border-right: 1px solid var(--jp-border-color2);
    background-color: var(--jp-layout-color0);
  }

  .jp-CollaboratorCursor {
    border-left: 5px solid transparent;
    border-right: 5px solid transparent;
    border-top: none;
    border-bottom: 3px solid;
    background-clip: content-box;
    margin-left: -5px;
    margin-right: -5px;
  }

  .CodeMirror-selectedtext.cm-searching {
    background-color: var(--jp-search-selected-match-background-color) !important;
    color: var(--jp-search-selected-match-color) !important;
  }

  .cm-searching {
    background-color: var(
      --jp-search-unselected-match-background-color
    ) !important;
    color: var(--jp-search-unselected-match-color) !important;
  }

  .CodeMirror-focused .CodeMirror-selected {
    background-color: var(--jp-editor-selected-focused-background);
  }

  .CodeMirror-selected {
    background-color: var(--jp-editor-selected-background);
  }

  .jp-CollaboratorCursor-hover {
    position: absolute;
    z-index: 1;
    transform: translateX(-50%);
    color: white;
    border-radius: 3px;
    padding-left: 4px;
    padding-right: 4px;
    padding-top: 1px;
    padding-bottom: 1px;
    text-align: center;
    font-size: var(--jp-ui-font-size1);
    white-space: nowrap;
  }

  .jp-CodeMirror-ruler {
    border-left: 1px dashed var(--jp-border-color2);
  }

  /**
  * Here is our jupyter theme for CodeMirror syntax highlighting
  * This is used in our marked.js syntax highlighting and CodeMirror itself
  * The string "jupyter" is set in ../codemirror/widget.DEFAULT_CODEMIRROR_THEME
  * This came from the classic notebook, which came form highlight.js/GitHub
  */

  /**
  * CodeMirror themes are handling the background/color in this way. This works
  * fine for CodeMirror editors outside the notebook, but the notebook styles
  * these things differently.
  */
  .CodeMirror.cm-s-jupyter {
    background: var(--jp-layout-color0);
    color: var(--jp-content-font-color1);
  }

  /* In the notebook, we want this styling to be handled by its container */
  .jp-CodeConsole .CodeMirror.cm-s-jupyter,
  .jp-Notebook .CodeMirror.cm-s-jupyter {
    background: transparent;
  }

  .cm-s-jupyter .CodeMirror-cursor {
    border-left: var(--jp-code-cursor-width0) solid var(--jp-editor-cursor-color);
  }
  .cm-s-jupyter span.cm-keyword {
    color: var(--jp-mirror-editor-keyword-color);
    font-weight: bold;
  }
  .cm-s-jupyter span.cm-atom {
    color: var(--jp-mirror-editor-atom-color);
  }
  .cm-s-jupyter span.cm-number {
    color: var(--jp-mirror-editor-number-color);
  }
  .cm-s-jupyter span.cm-def {
    color: var(--jp-mirror-editor-def-color);
  }
  .cm-s-jupyter span.cm-variable {
    color: var(--jp-mirror-editor-variable-color);
  }
  .cm-s-jupyter span.cm-variable-2 {
    color: var(--jp-mirror-editor-variable-2-color);
  }
  .cm-s-jupyter span.cm-variable-3 {
    color: var(--jp-mirror-editor-variable-3-color);
  }
  .cm-s-jupyter span.cm-punctuation {
    color: var(--jp-mirror-editor-punctuation-color);
  }
  .cm-s-jupyter span.cm-property {
    color: var(--jp-mirror-editor-property-color);
  }
  .cm-s-jupyter span.cm-operator {
    color: var(--jp-mirror-editor-operator-color);
    font-weight: bold;
  }
  .cm-s-jupyter span.cm-comment {
    color: var(--jp-mirror-editor-comment-color);
    font-style: italic;
  }
  .cm-s-jupyter span.cm-string {
    color: var(--jp-mirror-editor-string-color);
  }
  .cm-s-jupyter span.cm-string-2 {
    color: var(--jp-mirror-editor-string-2-color);
  }
  .cm-s-jupyter span.cm-meta {
    color: var(--jp-mirror-editor-meta-color);
  }
  .cm-s-jupyter span.cm-qualifier {
    color: var(--jp-mirror-editor-qualifier-color);
  }
  .cm-s-jupyter span.cm-builtin {
    color: var(--jp-mirror-editor-builtin-color);
  }
  .cm-s-jupyter span.cm-bracket {
    color: var(--jp-mirror-editor-bracket-color);
  }
  .cm-s-jupyter span.cm-tag {
    color: var(--jp-mirror-editor-tag-color);
  }
  .cm-s-jupyter span.cm-attribute {
    color: var(--jp-mirror-editor-attribute-color);
  }
  .cm-s-jupyter span.cm-header {
    color: var(--jp-mirror-editor-header-color);
  }
  .cm-s-jupyter span.cm-quote {
    color: var(--jp-mirror-editor-quote-color);
  }
  .cm-s-jupyter span.cm-link {
    color: var(--jp-mirror-editor-link-color);
  }
  .cm-s-jupyter span.cm-error {
    color: var(--jp-mirror-editor-error-color);
  }
  .cm-s-jupyter span.cm-hr {
    color: #999;
  }

  .cm-s-jupyter span.cm-tab {
    background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADAAAAAMCAYAAAAkuj5RAAAAAXNSR0IArs4c6QAAAGFJREFUSMft1LsRQFAQheHPowAKoACx3IgEKtaEHujDjORSgWTH/ZOdnZOcM/sgk/kFFWY0qV8foQwS4MKBCS3qR6ixBJvElOobYAtivseIE120FaowJPN75GMu8j/LfMwNjh4HUpwg4LUAAAAASUVORK5CYII=);
    background-position: right;
    background-repeat: no-repeat;
  }

  .cm-s-jupyter .CodeMirror-activeline-background,
  .cm-s-jupyter .CodeMirror-gutter {
    background-color: var(--jp-layout-color2);
  }

  /*-----------------------------------------------------------------------------
  | Copyright (c) Jupyter Development Team.
  | Distributed under the terms of the Modified BSD License.
  |----------------------------------------------------------------------------*/

  /*-----------------------------------------------------------------------------
  | RenderedText
  |----------------------------------------------------------------------------*/

  :root {
    /* This is the padding value to fill the gaps between lines containing spans with background color. */
    --jp-private-code-span-padding: calc(
      (var(--jp-code-line-height) - 1) * var(--jp-code-font-size) / 2
    );
  }

  .jp-RenderedText {
    text-align: left;
    padding-left: var(--jp-code-padding);
    line-height: var(--jp-code-line-height);
    font-family: var(--jp-code-font-family);
  }

  .jp-RenderedText pre,
  .jp-RenderedJavaScript pre,
  .jp-RenderedHTMLCommon pre {
    color: var(--jp-content-font-color1);
    font-size: var(--jp-code-font-size);
    border: none;
    margin: 0px;
    padding: 0px;
  }

  .jp-RenderedText pre a:link {
    text-decoration: none;
    color: var(--jp-content-link-color);
  }
  .jp-RenderedText pre a:hover {
    text-decoration: underline;
    color: var(--jp-content-link-color);
  }
  .jp-RenderedText pre a:visited {
    text-decoration: none;
    color: var(--jp-content-link-color);
  }

  /* console foregrounds and backgrounds */
  .jp-RenderedText pre .ansi-black-fg {
    color: #3e424d;
  }
  .jp-RenderedText pre .ansi-red-fg {
    color: #e75c58;
  }
  .jp-RenderedText pre .ansi-green-fg {
    color: #00a250;
  }
  .jp-RenderedText pre .ansi-yellow-fg {
    color: #ddb62b;
  }
  .jp-RenderedText pre .ansi-blue-fg {
    color: #208ffb;
  }
  .jp-RenderedText pre .ansi-magenta-fg {
    color: #d160c4;
  }
  .jp-RenderedText pre .ansi-cyan-fg {
    color: #60c6c8;
  }
  .jp-RenderedText pre .ansi-white-fg {
    color: #c5c1b4;
  }

  .jp-RenderedText pre .ansi-black-bg {
    background-color: #3e424d;
    padding: var(--jp-private-code-span-padding) 0;
  }
  .jp-RenderedText pre .ansi-red-bg {
    background-color: #e75c58;
    padding: var(--jp-private-code-span-padding) 0;
  }
  .jp-RenderedText pre .ansi-green-bg {
    background-color: #00a250;
    padding: var(--jp-private-code-span-padding) 0;
  }
  .jp-RenderedText pre .ansi-yellow-bg {
    background-color: #ddb62b;
    padding: var(--jp-private-code-span-padding) 0;
  }
  .jp-RenderedText pre .ansi-blue-bg {
    background-color: #208ffb;
    padding: var(--jp-private-code-span-padding) 0;
  }
  .jp-RenderedText pre .ansi-magenta-bg {
    background-color: #d160c4;
    padding: var(--jp-private-code-span-padding) 0;
  }
  .jp-RenderedText pre .ansi-cyan-bg {
    background-color: #60c6c8;
    padding: var(--jp-private-code-span-padding) 0;
  }
  .jp-RenderedText pre .ansi-white-bg {
    background-color: #c5c1b4;
    padding: var(--jp-private-code-span-padding) 0;
  }

  .jp-RenderedText pre .ansi-black-intense-fg {
    color: #282c36;
  }
  .jp-RenderedText pre .ansi-red-intense-fg {
    color: #b22b31;
  }
  .jp-RenderedText pre .ansi-green-intense-fg {
    color: #007427;
  }
  .jp-RenderedText pre .ansi-yellow-intense-fg {
    color: #b27d12;
  }
  .jp-RenderedText pre .ansi-blue-intense-fg {
    color: #0065ca;
  }
  .jp-RenderedText pre .ansi-magenta-intense-fg {
    color: #a03196;
  }
  .jp-RenderedText pre .ansi-cyan-intense-fg {
    color: #258f8f;
  }
  .jp-RenderedText pre .ansi-white-intense-fg {
    color: #a1a6b2;
  }

  .jp-RenderedText pre .ansi-black-intense-bg {
    background-color: #282c36;
    padding: var(--jp-private-code-span-padding) 0;
  }
  .jp-RenderedText pre .ansi-red-intense-bg {
    background-color: #b22b31;
    padding: var(--jp-private-code-span-padding) 0;
  }
  .jp-RenderedText pre .ansi-green-intense-bg {
    background-color: #007427;
    padding: var(--jp-private-code-span-padding) 0;
  }
  .jp-RenderedText pre .ansi-yellow-intense-bg {
    background-color: #b27d12;
    padding: var(--jp-private-code-span-padding) 0;
  }
  .jp-RenderedText pre .ansi-blue-intense-bg {
    background-color: #0065ca;
    padding: var(--jp-private-code-span-padding) 0;
  }
  .jp-RenderedText pre .ansi-magenta-intense-bg {
    background-color: #a03196;
    padding: var(--jp-private-code-span-padding) 0;
  }
  .jp-RenderedText pre .ansi-cyan-intense-bg {
    background-color: #258f8f;
    padding: var(--jp-private-code-span-padding) 0;
  }
  .jp-RenderedText pre .ansi-white-intense-bg {
    background-color: #a1a6b2;
    padding: var(--jp-private-code-span-padding) 0;
  }

  .jp-RenderedText pre .ansi-default-inverse-fg {
    color: var(--jp-ui-inverse-font-color0);
  }
  .jp-RenderedText pre .ansi-default-inverse-bg {
    background-color: var(--jp-inverse-layout-color0);
    padding: var(--jp-private-code-span-padding) 0;
  }

  .jp-RenderedText pre .ansi-bold {
    font-weight: bold;
  }
  .jp-RenderedText pre .ansi-underline {
    text-decoration: underline;
  }

  .jp-RenderedText[data-mime-type='application/vnd.jupyter.stderr'] {
    background: var(--jp-rendermime-error-background);
    padding-top: var(--jp-code-padding);
  }

  /*-----------------------------------------------------------------------------
  | RenderedLatex
  |----------------------------------------------------------------------------*/

  .jp-RenderedLatex {
    color: var(--jp-content-font-color1);
    font-size: var(--jp-content-font-size1);
    line-height: var(--jp-content-line-height);
  }

  /* Left-justify outputs.*/
  .jp-OutputArea-output.jp-RenderedLatex {
    padding: var(--jp-code-padding);
    text-align: left;
  }

  /*-----------------------------------------------------------------------------
  | RenderedHTML
  |----------------------------------------------------------------------------*/

  .jp-RenderedHTMLCommon {
    color: var(--jp-content-font-color1);
    font-family: var(--jp-content-font-family);
    font-size: var(--jp-content-font-size1);
    line-height: var(--jp-content-line-height);
    /* Give a bit more R padding on Markdown text to keep line lengths reasonable */
    padding-right: 20px;
  }

  .jp-RenderedHTMLCommon em {
    font-style: italic;
  }

  .jp-RenderedHTMLCommon strong {
    font-weight: bold;
  }

  .jp-RenderedHTMLCommon u {
    text-decoration: underline;
  }

  .jp-RenderedHTMLCommon a:link {
    text-decoration: none;
    color: var(--jp-content-link-color);
  }

  .jp-RenderedHTMLCommon a:hover {
    text-decoration: underline;
    color: var(--jp-content-link-color);
  }

  .jp-RenderedHTMLCommon a:visited {
    text-decoration: none;
    color: var(--jp-content-link-color);
  }

  /* Headings */

  .jp-RenderedHTMLCommon h1,
  .jp-RenderedHTMLCommon h2,
  .jp-RenderedHTMLCommon h3,
  .jp-RenderedHTMLCommon h4,
  .jp-RenderedHTMLCommon h5,
  .jp-RenderedHTMLCommon h6 {
    line-height: var(--jp-content-heading-line-height);
    font-weight: var(--jp-content-heading-font-weight);
    font-style: normal;
    margin: var(--jp-content-heading-margin-top) 0
      var(--jp-content-heading-margin-bottom) 0;
  }

  .jp-RenderedHTMLCommon h1:first-child,
  .jp-RenderedHTMLCommon h2:first-child,
  .jp-RenderedHTMLCommon h3:first-child,
  .jp-RenderedHTMLCommon h4:first-child,
  .jp-RenderedHTMLCommon h5:first-child,
  .jp-RenderedHTMLCommon h6:first-child {
    margin-top: calc(0.5 * var(--jp-content-heading-margin-top));
  }

  .jp-RenderedHTMLCommon h1:last-child,
  .jp-RenderedHTMLCommon h2:last-child,
  .jp-RenderedHTMLCommon h3:last-child,
  .jp-RenderedHTMLCommon h4:last-child,
  .jp-RenderedHTMLCommon h5:last-child,
  .jp-RenderedHTMLCommon h6:last-child {
    margin-bottom: calc(0.5 * var(--jp-content-heading-margin-bottom));
  }

  .jp-RenderedHTMLCommon h1 {
    font-size: var(--jp-content-font-size5);
  }

  .jp-RenderedHTMLCommon h2 {
    font-size: var(--jp-content-font-size4);
  }

  .jp-RenderedHTMLCommon h3 {
    font-size: var(--jp-content-font-size3);
  }

  .jp-RenderedHTMLCommon h4 {
    font-size: var(--jp-content-font-size2);
  }

  .jp-RenderedHTMLCommon h5 {
    font-size: var(--jp-content-font-size1);
  }

  .jp-RenderedHTMLCommon h6 {
    font-size: var(--jp-content-font-size0);
  }

  /* Lists */

  .jp-RenderedHTMLCommon ul:not(.list-inline),
  .jp-RenderedHTMLCommon ol:not(.list-inline) {
    padding-left: 2em;
  }

  .jp-RenderedHTMLCommon ul {
    list-style: disc;
  }

  .jp-RenderedHTMLCommon ul ul {
    list-style: square;
  }

  .jp-RenderedHTMLCommon ul ul ul {
    list-style: circle;
  }

  .jp-RenderedHTMLCommon ol {
    list-style: decimal;
  }

  .jp-RenderedHTMLCommon ol ol {
    list-style: upper-alpha;
  }

  .jp-RenderedHTMLCommon ol ol ol {
    list-style: lower-alpha;
  }

  .jp-RenderedHTMLCommon ol ol ol ol {
    list-style: lower-roman;
  }

  .jp-RenderedHTMLCommon ol ol ol ol ol {
    list-style: decimal;
  }

  .jp-RenderedHTMLCommon ol,
  .jp-RenderedHTMLCommon ul {
    margin-bottom: 1em;
  }

  .jp-RenderedHTMLCommon ul ul,
  .jp-RenderedHTMLCommon ul ol,
  .jp-RenderedHTMLCommon ol ul,
  .jp-RenderedHTMLCommon ol ol {
    margin-bottom: 0em;
  }

  .jp-RenderedHTMLCommon hr {
    color: var(--jp-border-color2);
    background-color: var(--jp-border-color1);
    margin-top: 1em;
    margin-bottom: 1em;
  }

  .jp-RenderedHTMLCommon > pre {
    margin: 1.5em 2em;
  }

  .jp-RenderedHTMLCommon pre,
  .jp-RenderedHTMLCommon code {
    border: 0;
    background-color: var(--jp-layout-color0);
    color: var(--jp-content-font-color1);
    font-family: var(--jp-code-font-family);
    font-size: inherit;
    line-height: var(--jp-code-line-height);
    padding: 0;
    white-space: pre-wrap;
  }

  .jp-RenderedHTMLCommon :not(pre) > code {
    background-color: var(--jp-layout-color2);
    padding: 1px 5px;
  }

  /* Tables */

  .jp-RenderedHTMLCommon table {
    border-collapse: collapse;
    border-spacing: 0;
    border: none;
    color: var(--jp-ui-font-color1);
    font-size: 12px;
    table-layout: fixed;
    margin-left: auto;
    margin-right: auto;
  }

  .jp-RenderedHTMLCommon thead {
    border-bottom: var(--jp-border-width) solid var(--jp-border-color1);
    vertical-align: bottom;
  }

  .jp-RenderedHTMLCommon td,
  .jp-RenderedHTMLCommon th,
  .jp-RenderedHTMLCommon tr {
    vertical-align: middle;
    padding: 0.5em 0.5em;
    line-height: normal;
    white-space: normal;
    max-width: none;
    border: none;
  }

  .jp-RenderedMarkdown.jp-RenderedHTMLCommon td,
  .jp-RenderedMarkdown.jp-RenderedHTMLCommon th {
    max-width: none;
  }

  :not(.jp-RenderedMarkdown).jp-RenderedHTMLCommon td,
  :not(.jp-RenderedMarkdown).jp-RenderedHTMLCommon th,
  :not(.jp-RenderedMarkdown).jp-RenderedHTMLCommon tr {
    text-align: right;
  }

  .jp-RenderedHTMLCommon th {
    font-weight: bold;
  }

  .jp-RenderedHTMLCommon tbody tr:nth-child(odd) {
    background: var(--jp-layout-color0);
  }

  .jp-RenderedHTMLCommon tbody tr:nth-child(even) {
    background: var(--jp-rendermime-table-row-background);
  }

  .jp-RenderedHTMLCommon tbody tr:hover {
    background: var(--jp-rendermime-table-row-hover-background);
  }

  .jp-RenderedHTMLCommon table {
    margin-bottom: 1em;
  }

  .jp-RenderedHTMLCommon p {
    text-align: left;
    margin: 0px;
  }

  .jp-RenderedHTMLCommon p {
    margin-bottom: 1em;
  }

  .jp-RenderedHTMLCommon img {
    -moz-force-broken-image-icon: 1;
  }

  /* Restrict to direct children as other images could be nested in other content. */
  .jp-RenderedHTMLCommon > img {
    display: block;
    margin-left: 0;
    margin-right: 0;
    margin-bottom: 1em;
  }

  /* Change color behind transparent images if they need it... */
  [data-jp-theme-light='false'] .jp-RenderedImage img.jp-needs-light-background {
    background-color: var(--jp-inverse-layout-color1);
  }
  [data-jp-theme-light='true'] .jp-RenderedImage img.jp-needs-dark-background {
    background-color: var(--jp-inverse-layout-color1);
  }
  /* ...or leave it untouched if they don't */
  [data-jp-theme-light='false'] .jp-RenderedImage img.jp-needs-dark-background {
  }
  [data-jp-theme-light='true'] .jp-RenderedImage img.jp-needs-light-background {
  }

  .jp-RenderedHTMLCommon img,
  .jp-RenderedImage img,
  .jp-RenderedHTMLCommon svg,
  .jp-RenderedSVG svg {
    max-width: 100%;
    height: auto;
  }

  .jp-RenderedHTMLCommon img.jp-mod-unconfined,
  .jp-RenderedImage img.jp-mod-unconfined,
  .jp-RenderedHTMLCommon svg.jp-mod-unconfined,
  .jp-RenderedSVG svg.jp-mod-unconfined {
    max-width: none;
  }

  .jp-RenderedHTMLCommon .alert {
    padding: var(--jp-notebook-padding);
    border: var(--jp-border-width) solid transparent;
    border-radius: var(--jp-border-radius);
    margin-bottom: 1em;
  }

  .jp-RenderedHTMLCommon .alert-info {
    color: var(--jp-info-color0);
    background-color: var(--jp-info-color3);
    border-color: var(--jp-info-color2);
  }
  .jp-RenderedHTMLCommon .alert-info hr {
    border-color: var(--jp-info-color3);
  }
  .jp-RenderedHTMLCommon .alert-info > p:last-child,
  .jp-RenderedHTMLCommon .alert-info > ul:last-child {
    margin-bottom: 0;
  }

  .jp-RenderedHTMLCommon .alert-warning {
    color: var(--jp-warn-color0);
    background-color: var(--jp-warn-color3);
    border-color: var(--jp-warn-color2);
  }
  .jp-RenderedHTMLCommon .alert-warning hr {
    border-color: var(--jp-warn-color3);
  }
  .jp-RenderedHTMLCommon .alert-warning > p:last-child,
  .jp-RenderedHTMLCommon .alert-warning > ul:last-child {
    margin-bottom: 0;
  }

  .jp-RenderedHTMLCommon .alert-success {
    color: var(--jp-success-color0);
    background-color: var(--jp-success-color3);
    border-color: var(--jp-success-color2);
  }
  .jp-RenderedHTMLCommon .alert-success hr {
    border-color: var(--jp-success-color3);
  }
  .jp-RenderedHTMLCommon .alert-success > p:last-child,
  .jp-RenderedHTMLCommon .alert-success > ul:last-child {
    margin-bottom: 0;
  }

  .jp-RenderedHTMLCommon .alert-danger {
    color: var(--jp-error-color0);
    background-color: var(--jp-error-color3);
    border-color: var(--jp-error-color2);
  }
  .jp-RenderedHTMLCommon .alert-danger hr {
    border-color: var(--jp-error-color3);
  }
  .jp-RenderedHTMLCommon .alert-danger > p:last-child,
  .jp-RenderedHTMLCommon .alert-danger > ul:last-child {
    margin-bottom: 0;
  }

  .jp-RenderedHTMLCommon blockquote {
    margin: 1em 2em;
    padding: 0 1em;
    border-left: 5px solid var(--jp-border-color2);
  }

  a.jp-InternalAnchorLink {
    visibility: hidden;
    margin-left: 8px;
    color: var(--md-blue-800);
  }

  h1:hover .jp-InternalAnchorLink,
  h2:hover .jp-InternalAnchorLink,
  h3:hover .jp-InternalAnchorLink,
  h4:hover .jp-InternalAnchorLink,
  h5:hover .jp-InternalAnchorLink,
  h6:hover .jp-InternalAnchorLink {
    visibility: visible;
  }

  .jp-RenderedHTMLCommon kbd {
    background-color: var(--jp-rendermime-table-row-background);
    border: 1px solid var(--jp-border-color0);
    border-bottom-color: var(--jp-border-color2);
    border-radius: 3px;
    box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.25);
    display: inline-block;
    font-size: 0.8em;
    line-height: 1em;
    padding: 0.2em 0.5em;
  }

  /* Most direct children of .jp-RenderedHTMLCommon have a margin-bottom of 1.0.
  * At the bottom of cells this is a bit too much as there is also spacing
  * between cells. Going all the way to 0 gets too tight between markdown and
  * code cells.
  */
  .jp-RenderedHTMLCommon > *:last-child {
    margin-bottom: 0.5em;
  }

  /*-----------------------------------------------------------------------------
  | Copyright (c) Jupyter Development Team.
  | Distributed under the terms of the Modified BSD License.
  |----------------------------------------------------------------------------*/

  .jp-MimeDocument {
    outline: none;
  }

  /*-----------------------------------------------------------------------------
  | Copyright (c) Jupyter Development Team.
  | Distributed under the terms of the Modified BSD License.
  |----------------------------------------------------------------------------*/

  /*-----------------------------------------------------------------------------
  | Variables
  |----------------------------------------------------------------------------*/

  :root {
    --jp-private-filebrowser-button-height: 28px;
    --jp-private-filebrowser-button-width: 48px;
  }

  /*-----------------------------------------------------------------------------
  | Copyright (c) Jupyter Development Team.
  | Distributed under the terms of the Modified BSD License.
  |----------------------------------------------------------------------------*/

  .jp-FileBrowser {
    display: flex;
    flex-direction: column;
    color: var(--jp-ui-font-color1);
    background: var(--jp-layout-color1);
    /* This is needed so that all font sizing of children done in ems is
    * relative to this base size */
    font-size: var(--jp-ui-font-size1);
  }

  .jp-FileBrowser-toolbar.jp-Toolbar {
    border-bottom: none;
    height: auto;
    margin: var(--jp-toolbar-header-margin);
    box-shadow: none;
  }

  .jp-BreadCrumbs {
    flex: 0 0 auto;
    margin: 8px 12px 8px 12px;
  }

  .jp-BreadCrumbs-item {
    margin: 0px 2px;
    padding: 0px 2px;
    border-radius: var(--jp-border-radius);
    cursor: pointer;
  }

  .jp-BreadCrumbs-item:hover {
    background-color: var(--jp-layout-color2);
  }

  .jp-BreadCrumbs-item:first-child {
    margin-left: 0px;
  }

  .jp-BreadCrumbs-item.jp-mod-dropTarget {
    background-color: var(--jp-brand-color2);
    opacity: 0.7;
  }

  /*-----------------------------------------------------------------------------
  | Buttons
  |----------------------------------------------------------------------------*/

  .jp-FileBrowser-toolbar.jp-Toolbar {
    padding: 0px;
    margin: 8px 12px 0px 12px;
  }

  .jp-FileBrowser-toolbar.jp-Toolbar {
    justify-content: flex-start;
  }

  .jp-FileBrowser-toolbar.jp-Toolbar .jp-Toolbar-item {
    flex: 0 0 auto;
    padding-left: 0px;
    padding-right: 2px;
  }

  .jp-FileBrowser-toolbar.jp-Toolbar .jp-ToolbarButtonComponent {
    width: 40px;
  }

  .jp-FileBrowser-toolbar.jp-Toolbar
    .jp-Toolbar-item:first-child
    .jp-ToolbarButtonComponent {
    width: 72px;
    background: var(--jp-brand-color1);
  }

  .jp-FileBrowser-toolbar.jp-Toolbar
    .jp-Toolbar-item:first-child
    .jp-ToolbarButtonComponent
    .jp-icon3 {
    fill: white;
  }

  /*-----------------------------------------------------------------------------
  | Other styles
  |----------------------------------------------------------------------------*/

  .jp-FileDialog.jp-mod-conflict input {
    color: red;
  }

  .jp-FileDialog .jp-new-name-title {
    margin-top: 12px;
  }

  .jp-LastModified-hidden {
    display: none;
  }

  .jp-FileBrowser-filterBox {
    padding: 0px;
    flex: 0 0 auto;
    margin: 8px 12px 0px 12px;
  }

  /*-----------------------------------------------------------------------------
  | DirListing
  |----------------------------------------------------------------------------*/

  .jp-DirListing {
    flex: 1 1 auto;
    display: flex;
    flex-direction: column;
    outline: 0;
  }

  .jp-DirListing-header {
    flex: 0 0 auto;
    display: flex;
    flex-direction: row;
    overflow: hidden;
    border-top: var(--jp-border-width) solid var(--jp-border-color2);
    border-bottom: var(--jp-border-width) solid var(--jp-border-color1);
    box-shadow: var(--jp-toolbar-box-shadow);
    z-index: 2;
  }

  .jp-DirListing-headerItem {
    padding: 4px 12px 2px 12px;
    font-weight: 500;
  }

  .jp-DirListing-headerItem:hover {
    background: var(--jp-layout-color2);
  }

  .jp-DirListing-headerItem.jp-id-name {
    flex: 1 0 84px;
  }

  .jp-DirListing-headerItem.jp-id-modified {
    flex: 0 0 112px;
    border-left: var(--jp-border-width) solid var(--jp-border-color2);
    text-align: right;
  }

  .jp-id-narrow {
    display: none;
    flex: 0 0 5px;
    padding: 4px 4px;
    border-left: var(--jp-border-width) solid var(--jp-border-color2);
    text-align: right;
    color: var(--jp-border-color2);
  }

  .jp-DirListing-narrow .jp-id-narrow {
    display: block;
  }

  .jp-DirListing-narrow .jp-id-modified,
  .jp-DirListing-narrow .jp-DirListing-itemModified {
    display: none;
  }

  .jp-DirListing-headerItem.jp-mod-selected {
    font-weight: 600;
  }

  /* increase specificity to override bundled default */
  .jp-DirListing-content {
    flex: 1 1 auto;
    margin: 0;
    padding: 0;
    list-style-type: none;
    overflow: auto;
    background-color: var(--jp-layout-color1);
  }

  .jp-DirListing-content mark {
    color: var(--jp-ui-font-color0);
    background-color: transparent;
    font-weight: bold;
  }

  /* Style the directory listing content when a user drops a file to upload */
  .jp-DirListing.jp-mod-native-drop .jp-DirListing-content {
    outline: 5px dashed rgba(128, 128, 128, 0.5);
    outline-offset: -10px;
    cursor: copy;
  }

  .jp-DirListing-item {
    display: flex;
    flex-direction: row;
    padding: 4px 12px;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
  }

  .jp-DirListing-item[data-is-dot] {
    opacity: 75%;
  }

  .jp-DirListing-item.jp-mod-selected {
    color: white;
    background: var(--jp-brand-color1);
  }

  .jp-DirListing-item.jp-mod-dropTarget {
    background: var(--jp-brand-color3);
  }

  .jp-DirListing-item:hover:not(.jp-mod-selected) {
    background: var(--jp-layout-color2);
  }

  .jp-DirListing-itemIcon {
    flex: 0 0 20px;
    margin-right: 4px;
  }

  .jp-DirListing-itemText {
    flex: 1 0 64px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    user-select: none;
  }

  .jp-DirListing-itemModified {
    flex: 0 0 125px;
    text-align: right;
  }

  .jp-DirListing-editor {
    flex: 1 0 64px;
    outline: none;
    border: none;
  }

  .jp-DirListing-item.jp-mod-running .jp-DirListing-itemIcon:before {
    color: limegreen;
    content: '\25CF';
    font-size: 8px;
    position: absolute;
    left: -8px;
  }

  .jp-DirListing-item.lm-mod-drag-image,
  .jp-DirListing-item.jp-mod-selected.lm-mod-drag-image {
    font-size: var(--jp-ui-font-size1);
    padding-left: 4px;
    margin-left: 4px;
    width: 160px;
    background-color: var(--jp-ui-inverse-font-color2);
    box-shadow: var(--jp-elevation-z2);
    border-radius: 0px;
    color: var(--jp-ui-font-color1);
    transform: translateX(-40%) translateY(-58%);
  }

  .jp-DirListing-deadSpace {
    flex: 1 1 auto;
    margin: 0;
    padding: 0;
    list-style-type: none;
    overflow: auto;
    background-color: var(--jp-layout-color1);
  }

  .jp-Document {
    min-width: 120px;
    min-height: 120px;
    outline: none;
  }

  /*-----------------------------------------------------------------------------
  | Copyright (c) Jupyter Development Team.
  | Distributed under the terms of the Modified BSD License.
  |----------------------------------------------------------------------------*/

  /*-----------------------------------------------------------------------------
  | Private CSS variables
  |----------------------------------------------------------------------------*/

  :root {
  }

  /*-----------------------------------------------------------------------------
  | Main OutputArea
  | OutputArea has a list of Outputs
  |----------------------------------------------------------------------------*/

  .jp-OutputArea {
    overflow-y: auto;
  }

  .jp-OutputArea-child {
    display: flex;
    flex-direction: row;
  }

  .jp-OutputPrompt {
    flex: 0 0 var(--jp-cell-prompt-width);
    color: var(--jp-cell-outprompt-font-color);
    font-family: var(--jp-cell-prompt-font-family);
    padding: var(--jp-code-padding);
    letter-spacing: var(--jp-cell-prompt-letter-spacing);
    line-height: var(--jp-code-line-height);
    font-size: var(--jp-code-font-size);
    border: var(--jp-border-width) solid transparent;
    opacity: var(--jp-cell-prompt-opacity);
    /* Right align prompt text, don't wrap to handle large prompt numbers */
    text-align: right;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    /* Disable text selection */
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
  }

  .jp-OutputArea-output {
    height: auto;
    overflow: auto;
    user-select: text;
    -moz-user-select: text;
    -webkit-user-select: text;
    -ms-user-select: text;
  }

  .jp-OutputArea-child .jp-OutputArea-output {
    flex-grow: 1;
    flex-shrink: 1;
  }

  /**
  * Isolated output.
  */
  .jp-OutputArea-output.jp-mod-isolated {
    width: 100%;
    display: block;
  }

  /*
  When drag events occur, `p-mod-override-cursor` is added to the body.
  Because iframes steal all cursor events, the following two rules are necessary
  to suppress pointer events while resize drags are occurring. There may be a
  better solution to this problem.
  */
  body.lm-mod-override-cursor .jp-OutputArea-output.jp-mod-isolated {
    position: relative;
  }

  body.lm-mod-override-cursor .jp-OutputArea-output.jp-mod-isolated:before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: transparent;
  }

  /* pre */

  .jp-OutputArea-output pre {
    border: none;
    margin: 0px;
    padding: 0px;
    overflow-x: auto;
    overflow-y: auto;
    word-break: break-all;
    word-wrap: break-word;
    white-space: pre-wrap;
  }

  /* tables */

  .jp-OutputArea-output.jp-RenderedHTMLCommon table {
    margin-left: 0;
    margin-right: 0;
  }

  /* description lists */

  .jp-OutputArea-output dl,
  .jp-OutputArea-output dt,
  .jp-OutputArea-output dd {
    display: block;
  }

  .jp-OutputArea-output dl {
    width: 100%;
    overflow: hidden;
    padding: 0;
    margin: 0;
  }

  .jp-OutputArea-output dt {
    font-weight: bold;
    float: left;
    width: 20%;
    padding: 0;
    margin: 0;
  }

  .jp-OutputArea-output dd {
    float: left;
    width: 80%;
    padding: 0;
    margin: 0;
  }

  /* Hide the gutter in case of
  *  - nested output areas (e.g. in the case of output widgets)
  *  - mirrored output areas
  */
  .jp-OutputArea .jp-OutputArea .jp-OutputArea-prompt {
    display: none;
  }

  /*-----------------------------------------------------------------------------
  | executeResult is added to any Output-result for the display of the object
  | returned by a cell
  |----------------------------------------------------------------------------*/

  .jp-OutputArea-output.jp-OutputArea-executeResult {
    margin-left: 0px;
    flex: 1 1 auto;
  }

  /* Text output with the Out[] prompt needs a top padding to match the
  * alignment of the Out[] prompt itself.
  */
  .jp-OutputArea-executeResult .jp-RenderedText.jp-OutputArea-output {
    padding-top: var(--jp-code-padding);
    border-top: var(--jp-border-width) solid transparent;
  }

  /*-----------------------------------------------------------------------------
  | The Stdin output
  |----------------------------------------------------------------------------*/

  .jp-OutputArea-stdin {
    line-height: var(--jp-code-line-height);
    padding-top: var(--jp-code-padding);
    display: flex;
  }

  .jp-Stdin-prompt {
    color: var(--jp-content-font-color0);
    padding-right: var(--jp-code-padding);
    vertical-align: baseline;
    flex: 0 0 auto;
  }

  .jp-Stdin-input {
    font-family: var(--jp-code-font-family);
    font-size: inherit;
    color: inherit;
    background-color: inherit;
    width: 42%;
    min-width: 200px;
    /* make sure input baseline aligns with prompt */
    vertical-align: baseline;
    /* padding + margin = 0.5em between prompt and cursor */
    padding: 0em 0.25em;
    margin: 0em 0.25em;
    flex: 0 0 70%;
  }

  .jp-Stdin-input:focus {
    box-shadow: none;
  }

  /*-----------------------------------------------------------------------------
  | Output Area View
  |----------------------------------------------------------------------------*/

  .jp-LinkedOutputView .jp-OutputArea {
    height: 100%;
    display: block;
  }

  .jp-LinkedOutputView .jp-OutputArea-output:only-child {
    height: 100%;
  }

  /*-----------------------------------------------------------------------------
  | Copyright (c) Jupyter Development Team.
  | Distributed under the terms of the Modified BSD License.
  |----------------------------------------------------------------------------*/

  .jp-Collapser {
    flex: 0 0 var(--jp-cell-collapser-width);
    padding: 0px;
    margin: 0px;
    border: none;
    outline: none;
    background: transparent;
    border-radius: var(--jp-border-radius);
    opacity: 1;
  }

  .jp-Collapser-child {
    display: block;
    width: 100%;
    box-sizing: border-box;
    /* height: 100% doesn't work because the height of its parent is computed from content */
    position: absolute;
    top: 0px;
    bottom: 0px;
  }

  /*-----------------------------------------------------------------------------
  | Copyright (c) Jupyter Development Team.
  | Distributed under the terms of the Modified BSD License.
  |----------------------------------------------------------------------------*/

  /*-----------------------------------------------------------------------------
  | Header/Footer
  |----------------------------------------------------------------------------*/

  /* Hidden by zero height by default */
  .jp-CellHeader,
  .jp-CellFooter {
    height: 0px;
    width: 100%;
    padding: 0px;
    margin: 0px;
    border: none;
    outline: none;
    background: transparent;
  }

  /*-----------------------------------------------------------------------------
  | Copyright (c) Jupyter Development Team.
  | Distributed under the terms of the Modified BSD License.
  |----------------------------------------------------------------------------*/

  /*-----------------------------------------------------------------------------
  | Input
  |----------------------------------------------------------------------------*/

  /* All input areas */
  .jp-InputArea {
    display: flex;
    flex-direction: row;
    overflow: hidden;
  }

  .jp-InputArea-editor {
    flex: 1 1 auto;
    overflow: hidden;
  }

  .jp-InputArea-editor {
    /* This is the non-active, default styling */
    border: var(--jp-border-width) solid var(--jp-cell-editor-border-color);
    border-radius: 0px;
    background: var(--jp-cell-editor-background);
  }

  .jp-InputPrompt {
    flex: 0 0 var(--jp-cell-prompt-width);
    color: var(--jp-cell-inprompt-font-color);
    font-family: var(--jp-cell-prompt-font-family);
    padding: var(--jp-code-padding);
    letter-spacing: var(--jp-cell-prompt-letter-spacing);
    opacity: var(--jp-cell-prompt-opacity);
    line-height: var(--jp-code-line-height);
    font-size: var(--jp-code-font-size);
    border: var(--jp-border-width) solid transparent;
    opacity: var(--jp-cell-prompt-opacity);
    /* Right align prompt text, don't wrap to handle large prompt numbers */
    text-align: right;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    /* Disable text selection */
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
  }

  /*-----------------------------------------------------------------------------
  | Copyright (c) Jupyter Development Team.
  | Distributed under the terms of the Modified BSD License.
  |----------------------------------------------------------------------------*/

  /*-----------------------------------------------------------------------------
  | Placeholder
  |----------------------------------------------------------------------------*/

  .jp-Placeholder {
    display: flex;
    flex-direction: row;
    flex: 1 1 auto;
  }

  .jp-Placeholder-prompt {
    box-sizing: border-box;
  }

  .jp-Placeholder-content {
    flex: 1 1 auto;
    border: none;
    background: transparent;
    height: 20px;
    box-sizing: border-box;
  }

  .jp-Placeholder-content .jp-MoreHorizIcon {
    width: 32px;
    height: 16px;
    border: 1px solid transparent;
    border-radius: var(--jp-border-radius);
  }

  .jp-Placeholder-content .jp-MoreHorizIcon:hover {
    border: 1px solid var(--jp-border-color1);
    box-shadow: 0px 0px 2px 0px rgba(0, 0, 0, 0.25);
    background-color: var(--jp-layout-color0);
  }

  /*-----------------------------------------------------------------------------
  | Copyright (c) Jupyter Development Team.
  | Distributed under the terms of the Modified BSD License.
  |----------------------------------------------------------------------------*/

  /*-----------------------------------------------------------------------------
  | Private CSS variables
  |----------------------------------------------------------------------------*/

  :root {
    --jp-private-cell-scrolling-output-offset: 5px;
  }

  /*-----------------------------------------------------------------------------
  | Cell
  |----------------------------------------------------------------------------*/

  .jp-Cell {
    padding: var(--jp-cell-padding);
    margin: 0px;
    border: none;
    outline: none;
    background: transparent;
  }

  /*-----------------------------------------------------------------------------
  | Common input/output
  |----------------------------------------------------------------------------*/

  .jp-Cell-inputWrapper,
  .jp-Cell-outputWrapper {
    display: flex;
    flex-direction: row;
    padding: 0px;
    margin: 0px;
    /* Added to reveal the box-shadow on the input and output collapsers. */
    overflow: visible;
  }

  /* Only input/output areas inside cells */
  .jp-Cell-inputArea,
  .jp-Cell-outputArea {
    flex: 1 1 auto;
  }

  /*-----------------------------------------------------------------------------
  | Collapser
  |----------------------------------------------------------------------------*/

  /* Make the output collapser disappear when there is not output, but do so
  * in a manner that leaves it in the layout and preserves its width.
  */
  .jp-Cell.jp-mod-noOutputs .jp-Cell-outputCollapser {
    border: none !important;
    background: transparent !important;
  }

  .jp-Cell:not(.jp-mod-noOutputs) .jp-Cell-outputCollapser {
    min-height: var(--jp-cell-collapser-min-height);
  }

  /*-----------------------------------------------------------------------------
  | Output
  |----------------------------------------------------------------------------*/

  /* Put a space between input and output when there IS output */
  .jp-Cell:not(.jp-mod-noOutputs) .jp-Cell-outputWrapper {
    margin-top: 5px;
  }

  .jp-CodeCell.jp-mod-outputsScrolled .jp-Cell-outputArea {
    overflow-y: auto;
    max-height: 200px;
    box-shadow: inset 0 0 6px 2px rgba(0, 0, 0, 0.3);
    margin-left: var(--jp-private-cell-scrolling-output-offset);
  }

  .jp-CodeCell.jp-mod-outputsScrolled .jp-OutputArea-prompt {
    flex: 0 0
      calc(
        var(--jp-cell-prompt-width) -
          var(--jp-private-cell-scrolling-output-offset)
      );
  }

  /*-----------------------------------------------------------------------------
  | CodeCell
  |----------------------------------------------------------------------------*/

  /*-----------------------------------------------------------------------------
  | MarkdownCell
  |----------------------------------------------------------------------------*/

  .jp-MarkdownOutput {
    flex: 1 1 auto;
    margin-top: 0;
    margin-bottom: 0;
    padding-left: var(--jp-code-padding);
  }

  .jp-MarkdownOutput.jp-RenderedHTMLCommon {
    overflow: auto;
  }

  /*-----------------------------------------------------------------------------
  | Copyright (c) Jupyter Development Team.
  | Distributed under the terms of the Modified BSD License.
  |----------------------------------------------------------------------------*/

  /*-----------------------------------------------------------------------------
  | Copyright (c) Jupyter Development Team.
  | Distributed under the terms of the Modified BSD License.
  |----------------------------------------------------------------------------*/

  /*-----------------------------------------------------------------------------
  | Variables
  |----------------------------------------------------------------------------*/

  /*-----------------------------------------------------------------------------

  /*-----------------------------------------------------------------------------
  | Styles
  |----------------------------------------------------------------------------*/

  .jp-NotebookPanel-toolbar {
    padding: 2px;
  }

  .jp-Toolbar-item.jp-Notebook-toolbarCellType .jp-select-wrapper.jp-mod-focused {
    border: none;
    box-shadow: none;
  }

  .jp-Notebook-toolbarCellTypeDropdown select {
    height: 24px;
    font-size: var(--jp-ui-font-size1);
    line-height: 14px;
    border-radius: 0;
    display: block;
  }

  .jp-Notebook-toolbarCellTypeDropdown span {
    top: 5px !important;
  }

  /*-----------------------------------------------------------------------------
  | Copyright (c) Jupyter Development Team.
  | Distributed under the terms of the Modified BSD License.
  |----------------------------------------------------------------------------*/

  /*-----------------------------------------------------------------------------
  | Private CSS variables
  |----------------------------------------------------------------------------*/

  :root {
    --jp-private-notebook-dragImage-width: 304px;
    --jp-private-notebook-dragImage-height: 36px;
    --jp-private-notebook-selected-color: var(--md-blue-400);
    --jp-private-notebook-active-color: var(--md-green-400);
  }

  /*-----------------------------------------------------------------------------
  | Imports
  |----------------------------------------------------------------------------*/

  /*-----------------------------------------------------------------------------
  | Notebook
  |----------------------------------------------------------------------------*/

  .jp-NotebookPanel {
    display: block;
    height: 100%;
  }

  .jp-NotebookPanel.jp-Document {
    min-width: 240px;
    min-height: 120px;
  }

  .jp-Notebook {
    padding: var(--jp-notebook-padding);
    outline: none;
    overflow: auto;
    background: var(--jp-layout-color0);
  }

  .jp-Notebook.jp-mod-scrollPastEnd::after {
    display: block;
    content: '';
    min-height: var(--jp-notebook-scroll-padding);
  }

  .jp-Notebook .jp-Cell {
    overflow: visible;
  }

  .jp-Notebook .jp-Cell .jp-InputPrompt {
    cursor: move;
  }

  /*-----------------------------------------------------------------------------
  | Notebook state related styling
  |
  | The notebook and cells each have states, here are the possibilities:
  |
  | - Notebook
  |   - Command
  |   - Edit
  | - Cell
  |   - None
  |   - Active (only one can be active)
  |   - Selected (the cells actions are applied to)
  |   - Multiselected (when multiple selected, the cursor)
  |   - No outputs
  |----------------------------------------------------------------------------*/

  /* Command or edit modes */

  .jp-Notebook .jp-Cell:not(.jp-mod-active) .jp-InputPrompt {
    opacity: var(--jp-cell-prompt-not-active-opacity);
    color: var(--jp-cell-prompt-not-active-font-color);
  }

  .jp-Notebook .jp-Cell:not(.jp-mod-active) .jp-OutputPrompt {
    opacity: var(--jp-cell-prompt-not-active-opacity);
    color: var(--jp-cell-prompt-not-active-font-color);
  }

  /* cell is active */
  .jp-Notebook .jp-Cell.jp-mod-active .jp-Collapser {
    background: var(--jp-brand-color1);
  }

  /* collapser is hovered */
  .jp-Notebook .jp-Cell .jp-Collapser:hover {
    box-shadow: var(--jp-elevation-z2);
    background: var(--jp-brand-color1);
    opacity: var(--jp-cell-collapser-not-active-hover-opacity);
  }

  /* cell is active and collapser is hovered */
  .jp-Notebook .jp-Cell.jp-mod-active .jp-Collapser:hover {
    background: var(--jp-brand-color0);
    opacity: 1;
  }

  /* Command mode */

  .jp-Notebook.jp-mod-commandMode .jp-Cell.jp-mod-selected {
    background: var(--jp-notebook-multiselected-color);
  }

  .jp-Notebook.jp-mod-commandMode
    .jp-Cell.jp-mod-active.jp-mod-selected:not(.jp-mod-multiSelected) {
    background: transparent;
  }

  /* Edit mode */

  .jp-Notebook.jp-mod-editMode .jp-Cell.jp-mod-active .jp-InputArea-editor {
    border: var(--jp-border-width) solid var(--jp-cell-editor-active-border-color);
    box-shadow: var(--jp-input-box-shadow);
    background-color: var(--jp-cell-editor-active-background);
  }

  /*-----------------------------------------------------------------------------
  | Notebook drag and drop
  |----------------------------------------------------------------------------*/

  .jp-Notebook-cell.jp-mod-dropSource {
    opacity: 0.5;
  }

  .jp-Notebook-cell.jp-mod-dropTarget,
  .jp-Notebook.jp-mod-commandMode
    .jp-Notebook-cell.jp-mod-active.jp-mod-selected.jp-mod-dropTarget {
    border-top-color: var(--jp-private-notebook-selected-color);
    border-top-style: solid;
    border-top-width: 2px;
  }

  .jp-dragImage {
    display: flex;
    flex-direction: row;
    width: var(--jp-private-notebook-dragImage-width);
    height: var(--jp-private-notebook-dragImage-height);
    border: var(--jp-border-width) solid var(--jp-cell-editor-border-color);
    background: var(--jp-cell-editor-background);
    overflow: visible;
  }

  .jp-dragImage-singlePrompt {
    box-shadow: 2px 2px 4px 0px rgba(0, 0, 0, 0.12);
  }

  .jp-dragImage .jp-dragImage-content {
    flex: 1 1 auto;
    z-index: 2;
    font-size: var(--jp-code-font-size);
    font-family: var(--jp-code-font-family);
    line-height: var(--jp-code-line-height);
    padding: var(--jp-code-padding);
    border: var(--jp-border-width) solid var(--jp-cell-editor-border-color);
    background: var(--jp-cell-editor-background-color);
    color: var(--jp-content-font-color3);
    text-align: left;
    margin: 4px 4px 4px 0px;
  }

  .jp-dragImage .jp-dragImage-prompt {
    flex: 0 0 auto;
    min-width: 36px;
    color: var(--jp-cell-inprompt-font-color);
    padding: var(--jp-code-padding);
    padding-left: 12px;
    font-family: var(--jp-cell-prompt-font-family);
    letter-spacing: var(--jp-cell-prompt-letter-spacing);
    line-height: 1.9;
    font-size: var(--jp-code-font-size);
    border: var(--jp-border-width) solid transparent;
  }

  .jp-dragImage-multipleBack {
    z-index: -1;
    position: absolute;
    height: 32px;
    width: 300px;
    top: 8px;
    left: 8px;
    background: var(--jp-layout-color2);
    border: var(--jp-border-width) solid var(--jp-input-border-color);
    box-shadow: 2px 2px 4px 0px rgba(0, 0, 0, 0.12);
  }

  /*-----------------------------------------------------------------------------
  | Cell toolbar
  |----------------------------------------------------------------------------*/

  .jp-NotebookTools {
    display: block;
    min-width: var(--jp-sidebar-min-width);
    color: var(--jp-ui-font-color1);
    background: var(--jp-layout-color1);
    /* This is needed so that all font sizing of children done in ems is
      * relative to this base size */
    font-size: var(--jp-ui-font-size1);
    overflow: auto;
  }

  .jp-NotebookTools-tool {
    padding: 0px 12px 0 12px;
  }

  .jp-ActiveCellTool {
    padding: 12px;
    background-color: var(--jp-layout-color1);
    border-top: none !important;
  }

  .jp-ActiveCellTool .jp-InputArea-prompt {
    flex: 0 0 auto;
    padding-left: 0px;
  }

  .jp-ActiveCellTool .jp-InputArea-editor {
    flex: 1 1 auto;
    background: var(--jp-cell-editor-background);
    border-color: var(--jp-cell-editor-border-color);
  }

  .jp-ActiveCellTool .jp-InputArea-editor .CodeMirror {
    background: transparent;
  }

  .jp-MetadataEditorTool {
    flex-direction: column;
    padding: 12px 0px 12px 0px;
  }

  .jp-RankedPanel > :not(:first-child) {
    margin-top: 12px;
  }

  .jp-KeySelector select.jp-mod-styled {
    font-size: var(--jp-ui-font-size1);
    color: var(--jp-ui-font-color0);
    border: var(--jp-border-width) solid var(--jp-border-color1);
  }

  .jp-KeySelector label,
  .jp-MetadataEditorTool label {
    line-height: 1.4;
  }

  .jp-NotebookTools .jp-select-wrapper {
    margin-top: 4px;
    margin-bottom: 0px;
  }

  .jp-NotebookTools .jp-Collapse {
    margin-top: 16px;
  }

  /*-----------------------------------------------------------------------------
  | Presentation Mode (.jp-mod-presentationMode)
  |----------------------------------------------------------------------------*/

  .jp-mod-presentationMode .jp-Notebook {
    --jp-content-font-size1: var(--jp-content-presentation-font-size1);
    --jp-code-font-size: var(--jp-code-presentation-font-size);
  }

  .jp-mod-presentationMode .jp-Notebook .jp-Cell .jp-InputPrompt,
  .jp-mod-presentationMode .jp-Notebook .jp-Cell .jp-OutputPrompt {
    flex: 0 0 110px;
  }

  </style>

      <style type="text/css">
  /*-----------------------------------------------------------------------------
  | Copyright (c) Jupyter Development Team.
  | Distributed under the terms of the Modified BSD License.
  |----------------------------------------------------------------------------*/

  /*
  The following CSS variables define the main, public API for styling JupyterLab.
  These variables should be used by all plugins wherever possible. In other
  words, plugins should not define custom colors, sizes, etc unless absolutely
  necessary. This enables users to change the visual theme of JupyterLab
  by changing these variables.

  Many variables appear in an ordered sequence (0,1,2,3). These sequences
  are designed to work well together, so for example, `--jp-border-color1` should
  be used with `--jp-layout-color1`. The numbers have the following meanings:

  * 0: super-primary, reserved for special emphasis
  * 1: primary, most important under normal situations
  * 2: secondary, next most important under normal situations
  * 3: tertiary, next most important under normal situations

  Throughout JupyterLab, we are mostly following principles from Google's
  Material Design when selecting colors. We are not, however, following
  all of MD as it is not optimized for dense, information rich UIs.
  */

  :root {
    /* Elevation
    *
    * We style box-shadows using Material Design's idea of elevation. These particular numbers are taken from here:
    *
    * https://github.com/material-components/material-components-web
    * https://material-components-web.appspot.com/elevation.html
    */

    --jp-shadow-base-lightness: 0;
    --jp-shadow-umbra-color: rgba(
      var(--jp-shadow-base-lightness),
      var(--jp-shadow-base-lightness),
      var(--jp-shadow-base-lightness),
      0.2
    );
    --jp-shadow-penumbra-color: rgba(
      var(--jp-shadow-base-lightness),
      var(--jp-shadow-base-lightness),
      var(--jp-shadow-base-lightness),
      0.14
    );
    --jp-shadow-ambient-color: rgba(
      var(--jp-shadow-base-lightness),
      var(--jp-shadow-base-lightness),
      var(--jp-shadow-base-lightness),
      0.12
    );
    --jp-elevation-z0: none;
    --jp-elevation-z1: 0px 2px 1px -1px var(--jp-shadow-umbra-color),
      0px 1px 1px 0px var(--jp-shadow-penumbra-color),
      0px 1px 3px 0px var(--jp-shadow-ambient-color);
    --jp-elevation-z2: 0px 3px 1px -2px var(--jp-shadow-umbra-color),
      0px 2px 2px 0px var(--jp-shadow-penumbra-color),
      0px 1px 5px 0px var(--jp-shadow-ambient-color);
    --jp-elevation-z4: 0px 2px 4px -1px var(--jp-shadow-umbra-color),
      0px 4px 5px 0px var(--jp-shadow-penumbra-color),
      0px 1px 10px 0px var(--jp-shadow-ambient-color);
    --jp-elevation-z6: 0px 3px 5px -1px var(--jp-shadow-umbra-color),
      0px 6px 10px 0px var(--jp-shadow-penumbra-color),
      0px 1px 18px 0px var(--jp-shadow-ambient-color);
    --jp-elevation-z8: 0px 5px 5px -3px var(--jp-shadow-umbra-color),
      0px 8px 10px 1px var(--jp-shadow-penumbra-color),
      0px 3px 14px 2px var(--jp-shadow-ambient-color);
    --jp-elevation-z12: 0px 7px 8px -4px var(--jp-shadow-umbra-color),
      0px 12px 17px 2px var(--jp-shadow-penumbra-color),
      0px 5px 22px 4px var(--jp-shadow-ambient-color);
    --jp-elevation-z16: 0px 8px 10px -5px var(--jp-shadow-umbra-color),
      0px 16px 24px 2px var(--jp-shadow-penumbra-color),
      0px 6px 30px 5px var(--jp-shadow-ambient-color);
    --jp-elevation-z20: 0px 10px 13px -6px var(--jp-shadow-umbra-color),
      0px 20px 31px 3px var(--jp-shadow-penumbra-color),
      0px 8px 38px 7px var(--jp-shadow-ambient-color);
    --jp-elevation-z24: 0px 11px 15px -7px var(--jp-shadow-umbra-color),
      0px 24px 38px 3px var(--jp-shadow-penumbra-color),
      0px 9px 46px 8px var(--jp-shadow-ambient-color);

    /* Borders
    *
    * The following variables, specify the visual styling of borders in JupyterLab.
    */

    --jp-border-width: 1px;
    --jp-border-color0: var(--md-grey-400);
    --jp-border-color1: var(--md-grey-400);
    --jp-border-color2: var(--md-grey-300);
    --jp-border-color3: var(--md-grey-200);
    --jp-border-radius: 2px;

    /* UI Fonts
    *
    * The UI font CSS variables are used for the typography all of the JupyterLab
    * user interface elements that are not directly user generated content.
    *
    * The font sizing here is done assuming that the body font size of --jp-ui-font-size1
    * is applied to a parent element. When children elements, such as headings, are sized
    * in em all things will be computed relative to that body size.
    */

    --jp-ui-font-scale-factor: 1.2;
    --jp-ui-font-size0: 0.83333em;
    --jp-ui-font-size1: 13px; /* Base font size */
    --jp-ui-font-size2: 1.2em;
    --jp-ui-font-size3: 1.44em;

    --jp-ui-font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Helvetica,
      Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol';

    /*
    * Use these font colors against the corresponding main layout colors.
    * In a light theme, these go from dark to light.
    */

    /* Defaults use Material Design specification */
    --jp-ui-font-color0: rgba(0, 0, 0, 1);
    --jp-ui-font-color1: rgba(0, 0, 0, 0.87);
    --jp-ui-font-color2: rgba(0, 0, 0, 0.54);
    --jp-ui-font-color3: rgba(0, 0, 0, 0.38);

    /*
    * Use these against the brand/accent/warn/error colors.
    * These will typically go from light to darker, in both a dark and light theme.
    */

    --jp-ui-inverse-font-color0: rgba(255, 255, 255, 1);
    --jp-ui-inverse-font-color1: rgba(255, 255, 255, 1);
    --jp-ui-inverse-font-color2: rgba(255, 255, 255, 0.7);
    --jp-ui-inverse-font-color3: rgba(255, 255, 255, 0.5);

    /* Content Fonts
    *
    * Content font variables are used for typography of user generated content.
    *
    * The font sizing here is done assuming that the body font size of --jp-content-font-size1
    * is applied to a parent element. When children elements, such as headings, are sized
    * in em all things will be computed relative to that body size.
    */

    --jp-content-line-height: 1.6;
    --jp-content-font-scale-factor: 1.2;
    --jp-content-font-size0: 0.83333em;
    --jp-content-font-size1: 14px; /* Base font size */
    --jp-content-font-size2: 1.2em;
    --jp-content-font-size3: 1.44em;
    --jp-content-font-size4: 1.728em;
    --jp-content-font-size5: 2.0736em;

    /* This gives a magnification of about 125% in presentation mode over normal. */
    --jp-content-presentation-font-size1: 17px;

    --jp-content-heading-line-height: 1;
    --jp-content-heading-margin-top: 1.2em;
    --jp-content-heading-margin-bottom: 0.8em;
    --jp-content-heading-font-weight: 500;

    /* Defaults use Material Design specification */
    --jp-content-font-color0: rgba(0, 0, 0, 1);
    --jp-content-font-color1: rgba(0, 0, 0, 0.87);
    --jp-content-font-color2: rgba(0, 0, 0, 0.54);
    --jp-content-font-color3: rgba(0, 0, 0, 0.38);

    --jp-content-link-color: var(--md-blue-700);

    --jp-content-font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI',
      Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji',
      'Segoe UI Symbol';

    /*
    * Code Fonts
    *
    * Code font variables are used for typography of code and other monospaces content.
    */

    --jp-code-font-size: 13px;
    --jp-code-line-height: 1.3077; /* 17px for 13px base */
    --jp-code-padding: 5px; /* 5px for 13px base, codemirror highlighting needs integer px value */
    --jp-code-font-family-default: Menlo, Consolas, 'DejaVu Sans Mono', monospace;
    --jp-code-font-family: var(--jp-code-font-family-default);

    /* This gives a magnification of about 125% in presentation mode over normal. */
    --jp-code-presentation-font-size: 16px;

    /* may need to tweak cursor width if you change font size */
    --jp-code-cursor-width0: 1.4px;
    --jp-code-cursor-width1: 2px;
    --jp-code-cursor-width2: 4px;

    /* Layout
    *
    * The following are the main layout colors use in JupyterLab. In a light
    * theme these would go from light to dark.
    */

    --jp-layout-color0: white;
    --jp-layout-color1: white;
    --jp-layout-color2: var(--md-grey-200);
    --jp-layout-color3: var(--md-grey-400);
    --jp-layout-color4: var(--md-grey-600);

    /* Inverse Layout
    *
    * The following are the inverse layout colors use in JupyterLab. In a light
    * theme these would go from dark to light.
    */

    --jp-inverse-layout-color0: #111111;
    --jp-inverse-layout-color1: var(--md-grey-900);
    --jp-inverse-layout-color2: var(--md-grey-800);
    --jp-inverse-layout-color3: var(--md-grey-700);
    --jp-inverse-layout-color4: var(--md-grey-600);

    /* Brand/accent */

    --jp-brand-color0: var(--md-blue-700);
    --jp-brand-color1: var(--md-blue-500);
    --jp-brand-color2: var(--md-blue-300);
    --jp-brand-color3: var(--md-blue-100);
    --jp-brand-color4: var(--md-blue-50);

    --jp-accent-color0: var(--md-green-700);
    --jp-accent-color1: var(--md-green-500);
    --jp-accent-color2: var(--md-green-300);
    --jp-accent-color3: var(--md-green-100);

    /* State colors (warn, error, success, info) */

    --jp-warn-color0: var(--md-orange-700);
    --jp-warn-color1: var(--md-orange-500);
    --jp-warn-color2: var(--md-orange-300);
    --jp-warn-color3: var(--md-orange-100);

    --jp-error-color0: var(--md-red-700);
    --jp-error-color1: var(--md-red-500);
    --jp-error-color2: var(--md-red-300);
    --jp-error-color3: var(--md-red-100);

    --jp-success-color0: var(--md-green-700);
    --jp-success-color1: var(--md-green-500);
    --jp-success-color2: var(--md-green-300);
    --jp-success-color3: var(--md-green-100);

    --jp-info-color0: var(--md-cyan-700);
    --jp-info-color1: var(--md-cyan-500);
    --jp-info-color2: var(--md-cyan-300);
    --jp-info-color3: var(--md-cyan-100);

    /* Cell specific styles */

    --jp-cell-padding: 5px;

    --jp-cell-collapser-width: 8px;
    --jp-cell-collapser-min-height: 20px;
    --jp-cell-collapser-not-active-hover-opacity: 0.6;

    --jp-cell-editor-background: var(--md-grey-100);
    --jp-cell-editor-border-color: var(--md-grey-300);
    --jp-cell-editor-box-shadow: inset 0 0 2px var(--md-blue-300);
    --jp-cell-editor-active-background: var(--jp-layout-color0);
    --jp-cell-editor-active-border-color: var(--jp-brand-color1);

    --jp-cell-prompt-width: 64px;
    --jp-cell-prompt-font-family: var(--jp-code-font-family-default);
    --jp-cell-prompt-letter-spacing: 0px;
    --jp-cell-prompt-opacity: 1;
    --jp-cell-prompt-not-active-opacity: 0.5;
    --jp-cell-prompt-not-active-font-color: var(--md-grey-700);
    /* A custom blend of MD grey and blue 600
    * See https://meyerweb.com/eric/tools/color-blend/#546E7A:1E88E5:5:hex */
    --jp-cell-inprompt-font-color: #307fc1;
    /* A custom blend of MD grey and orange 600
    * https://meyerweb.com/eric/tools/color-blend/#546E7A:F4511E:5:hex */
    --jp-cell-outprompt-font-color: #bf5b3d;

    /* Notebook specific styles */

    --jp-notebook-padding: 10px;
    --jp-notebook-select-background: var(--jp-layout-color1);
    --jp-notebook-multiselected-color: var(--md-blue-50);

    /* The scroll padding is calculated to fill enough space at the bottom of the
    notebook to show one single-line cell (with appropriate padding) at the top
    when the notebook is scrolled all the way to the bottom. We also subtract one
    pixel so that no scrollbar appears if we have just one single-line cell in the
    notebook. This padding is to enable a 'scroll past end' feature in a notebook.
    */
    --jp-notebook-scroll-padding: calc(
      100% - var(--jp-code-font-size) * var(--jp-code-line-height) -
        var(--jp-code-padding) - var(--jp-cell-padding) - 1px
    );

    /* Rendermime styles */

    --jp-rendermime-error-background: #fdd;
    --jp-rendermime-table-row-background: var(--md-grey-100);
    --jp-rendermime-table-row-hover-background: var(--md-light-blue-50);

    /* Dialog specific styles */

    --jp-dialog-background: rgba(0, 0, 0, 0.25);

    /* Console specific styles */

    --jp-console-padding: 10px;

    /* Toolbar specific styles */

    --jp-toolbar-border-color: var(--jp-border-color1);
    --jp-toolbar-micro-height: 8px;
    --jp-toolbar-background: var(--jp-layout-color1);
    --jp-toolbar-box-shadow: 0px 0px 2px 0px rgba(0, 0, 0, 0.24);
    --jp-toolbar-header-margin: 4px 4px 0px 4px;
    --jp-toolbar-active-background: var(--md-grey-300);

    /* Input field styles */

    --jp-input-box-shadow: inset 0 0 2px var(--md-blue-300);
    --jp-input-active-background: var(--jp-layout-color1);
    --jp-input-hover-background: var(--jp-layout-color1);
    --jp-input-background: var(--md-grey-100);
    --jp-input-border-color: var(--jp-border-color1);
    --jp-input-active-border-color: var(--jp-brand-color1);
    --jp-input-active-box-shadow-color: rgba(19, 124, 189, 0.3);

    /* General editor styles */

    --jp-editor-selected-background: #d9d9d9;
    --jp-editor-selected-focused-background: #d7d4f0;
    --jp-editor-cursor-color: var(--jp-ui-font-color0);

    /* Code mirror specific styles */

    --jp-mirror-editor-keyword-color: #008000;
    --jp-mirror-editor-atom-color: #88f;
    --jp-mirror-editor-number-color: #080;
    --jp-mirror-editor-def-color: #00f;
    --jp-mirror-editor-variable-color: var(--md-grey-900);
    --jp-mirror-editor-variable-2-color: #05a;
    --jp-mirror-editor-variable-3-color: #085;
    --jp-mirror-editor-punctuation-color: #05a;
    --jp-mirror-editor-property-color: #05a;
    --jp-mirror-editor-operator-color: #aa22ff;
    --jp-mirror-editor-comment-color: #408080;
    --jp-mirror-editor-string-color: #ba2121;
    --jp-mirror-editor-string-2-color: #708;
    --jp-mirror-editor-meta-color: #aa22ff;
    --jp-mirror-editor-qualifier-color: #555;
    --jp-mirror-editor-builtin-color: #008000;
    --jp-mirror-editor-bracket-color: #997;
    --jp-mirror-editor-tag-color: #170;
    --jp-mirror-editor-attribute-color: #00c;
    --jp-mirror-editor-header-color: blue;
    --jp-mirror-editor-quote-color: #090;
    --jp-mirror-editor-link-color: #00c;
    --jp-mirror-editor-error-color: #f00;
    --jp-mirror-editor-hr-color: #999;

    /* Vega extension styles */

    --jp-vega-background: white;

    /* Sidebar-related styles */

    --jp-sidebar-min-width: 250px;

    /* Search-related styles */

    --jp-search-toggle-off-opacity: 0.5;
    --jp-search-toggle-hover-opacity: 0.8;
    --jp-search-toggle-on-opacity: 1;
    --jp-search-selected-match-background-color: rgb(245, 200, 0);
    --jp-search-selected-match-color: black;
    --jp-search-unselected-match-background-color: var(
      --jp-inverse-layout-color0
    );
    --jp-search-unselected-match-color: var(--jp-ui-inverse-font-color0);

    /* Icon colors that work well with light or dark backgrounds */
    --jp-icon-contrast-color0: var(--md-purple-600);
    --jp-icon-contrast-color1: var(--md-green-600);
    --jp-icon-contrast-color2: var(--md-pink-600);
    --jp-icon-contrast-color3: var(--md-blue-600);
  }
  </style>

  <style type="text/css">
  a.anchor-link {
    display: none;
  }
  .highlight  {
      margin: 0.4em;
  }

  /* Input area styling */
  .jp-InputArea {
      overflow: hidden;
  }

  .jp-InputArea-editor {
      overflow: hidden;
  }

  @media print {
    body {
      margin: 0;
    }
  }
  </style>

  <!-- Load mathjax -->
      <script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.7/latest.js?config=TeX-MML-AM_CHTML-full,Safe"> </script>
      <!-- MathJax configuration -->
      <script type="text/x-mathjax-config">
      init_mathjax = function() {
          if (window.MathJax) {
          // MathJax loaded
              MathJax.Hub.Config({
                  TeX: {
                      equationNumbers: {
                      autoNumber: "AMS",
                      useLabelIds: true
                      }
                  },
                  tex2jax: {
                      inlineMath: [ ['$','$'], ["\\(","\\)"] ],
                      displayMath: [ ['$$','$$'], ["\\[","\\]"] ],
                      processEscapes: true,
                      processEnvironments: true
                  },
                  displayAlign: 'center',
                  CommonHTML: {
                      linebreaks: { 
                      automatic: true 
                      }
                  },
                  "HTML-CSS": {
                      linebreaks: { 
                      automatic: true 
                      }
                  }
              });
          
              MathJax.Hub.Queue(["Typeset", MathJax.Hub]);
          }
      }
      init_mathjax();
      </script>
      <!-- End of mathjax configuration --></head>
  <body class="jp-Notebook" data-jp-theme-light="true" data-jp-theme-name="JupyterLab Light">
  <div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
  <div class="jp-Cell-inputWrapper">
  <div class="jp-InputArea jp-Cell-inputArea">
  <div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[&nbsp;]:</div>
  <div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
      <div class="CodeMirror cm-s-jupyter">
  <div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">tensorflow.keras.models</span> <span class="kn">import</span> <span class="n">Sequential</span>
  <span class="kn">from</span> <span class="nn">tensorflow.keras.layers</span> <span class="kn">import</span> <span class="n">Dense</span><span class="p">,</span> <span class="n">Activation</span>
  <span class="kn">from</span> <span class="nn">tensorflow.keras.utils</span> <span class="kn">import</span> <span class="n">to_categorical</span>
  <span class="kn">from</span> <span class="nn">tensorflow.keras.datasets</span> <span class="kn">import</span> <span class="n">mnist</span>
  <span class="kn">import</span> <span class="nn">numpy</span> <span class="k">as</span> <span class="nn">np</span>
  <span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>
  </pre></div>

      </div>
  </div>
  </div>
  </div>

  </div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
  <div class="jp-Cell-inputWrapper">
  <div class="jp-InputArea jp-Cell-inputArea">
  <div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[&nbsp;]:</div>
  <div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
      <div class="CodeMirror cm-s-jupyter">
  <div class=" highlight hl-ipython3"><pre><span></span><span class="p">(</span><span class="n">x_train</span><span class="p">,</span> <span class="n">y_train</span><span class="p">),</span> <span class="p">(</span><span class="n">x_test</span><span class="p">,</span> <span class="n">y_test</span><span class="p">)</span> <span class="o">=</span> <span class="n">mnist</span><span class="o">.</span><span class="n">load_data</span><span class="p">()</span>
  <span class="nb">print</span><span class="p">(</span><span class="s2">&quot;x_train shape&quot;</span><span class="p">,</span> <span class="n">x_train</span><span class="o">.</span><span class="n">shape</span><span class="p">)</span>
  <span class="nb">print</span><span class="p">(</span><span class="s2">&quot;y_train shape&quot;</span><span class="p">,</span> <span class="n">y_train</span><span class="o">.</span><span class="n">shape</span><span class="p">)</span>
  <span class="nb">print</span><span class="p">(</span><span class="s2">&quot;x_test shape&quot;</span><span class="p">,</span> <span class="n">x_test</span><span class="o">.</span><span class="n">shape</span><span class="p">)</span>
  <span class="nb">print</span><span class="p">(</span><span class="s2">&quot;y_test shape&quot;</span><span class="p">,</span> <span class="n">y_test</span><span class="o">.</span><span class="n">shape</span><span class="p">)</span>
  </pre></div>

      </div>
  </div>
  </div>
  </div>

  <div class="jp-Cell-outputWrapper">


  <div class="jp-OutputArea jp-Cell-outputArea">

  <div class="jp-OutputArea-child">

      
      <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>


  <div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain">
  <pre>Downloading data from https://storage.googleapis.com/tensorflow/tf-keras-datasets/mnist.npz
  <span class="ansi-bold">11490434/11490434</span> <span class="ansi-green-fg">━━━━━━━━━━━━━━━━━━━━</span> <span class="ansi-bold">0s</span> 0us/step
  x_train shape (60000, 28, 28)
  y_train shape (60000,)
  x_test shape (10000, 28, 28)
  y_test shape (10000,)
  </pre>
  </div>
  </div>

  </div>

  </div>

  </div>
  <div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
  </div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
  <p>MNIST 데이터셋 불러오기</p>
  <p>MNIST: 손으로 쓴 숫자(0~9) 이미지 데이터 70,000개 모아놓은 데이터셋.</p>
  <p>x_train: 훈련용 이미지 (60,000개)</p>
  <p>y_train: 훈련용 정답 레이블 (60,000개)</p>
  <p>x_test: 테스트용 이미지 (10,000개)</p>
  <p>y_test: 테스트용 정답 레이블 (10,000개)</p>
  <p>이미지는 (28x28) 크기의 흑백사진</p>

  </div>
  </div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
  <div class="jp-Cell-inputWrapper">
  <div class="jp-InputArea jp-Cell-inputArea">
  <div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[&nbsp;]:</div>
  <div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
      <div class="CodeMirror cm-s-jupyter">
  <div class=" highlight hl-ipython3"><pre><span></span><span class="n">X_train</span> <span class="o">=</span> <span class="n">x_train</span><span class="o">.</span><span class="n">reshape</span><span class="p">(</span><span class="mi">60000</span><span class="p">,</span> <span class="mi">784</span><span class="p">)</span>
  <span class="n">X_test</span> <span class="o">=</span> <span class="n">x_test</span><span class="o">.</span><span class="n">reshape</span><span class="p">(</span><span class="mi">10000</span><span class="p">,</span> <span class="mi">784</span><span class="p">)</span>
  <span class="n">X_train</span> <span class="o">=</span> <span class="n">X_train</span><span class="o">.</span><span class="n">astype</span><span class="p">(</span><span class="s1">&#39;float32&#39;</span><span class="p">)</span>
  <span class="n">X_test</span> <span class="o">=</span> <span class="n">X_test</span><span class="o">.</span><span class="n">astype</span><span class="p">(</span><span class="s1">&#39;float32&#39;</span><span class="p">)</span>
  <span class="n">X_train</span> <span class="o">/=</span> <span class="mi">255</span>
  <span class="n">X_test</span> <span class="o">/=</span> <span class="mi">255</span>
  <span class="nb">print</span><span class="p">(</span><span class="s2">&quot;X Training matrix shape&quot;</span><span class="p">,</span> <span class="n">X_train</span><span class="o">.</span><span class="n">shape</span><span class="p">)</span>
  <span class="nb">print</span><span class="p">(</span><span class="s2">&quot;X Testing matrix shape&quot;</span><span class="p">,</span> <span class="n">X_test</span><span class="o">.</span><span class="n">shape</span><span class="p">)</span>
  </pre></div>

      </div>
  </div>
  </div>
  </div>

  <div class="jp-Cell-outputWrapper">


  <div class="jp-OutputArea jp-Cell-outputArea">

  <div class="jp-OutputArea-child">

      
      <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>


  <div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain">
  <pre>X Training matrix shape (60000, 784)
  X Testing matrix shape (10000, 784)
  </pre>
  </div>
  </div>

  </div>

  </div>

  </div>
  <div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
  </div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
  <p>데이터 전처리 (Reshape + 정규화)</p>
  <p><strong>28x28 이미지를 1차원 벡터(784개)</strong>로 펴는 작업 (딥러닝에 넣기 편하게 만듦).</p>
  <p>255로 나누기: 픽셀 값(0255)을 01 사이로 바꿔서 학습하기 쉽게 만듦.</p>

  </div>
  </div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
  <div class="jp-Cell-inputWrapper">
  <div class="jp-InputArea jp-Cell-inputArea">
  <div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[&nbsp;]:</div>
  <div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
      <div class="CodeMirror cm-s-jupyter">
  <div class=" highlight hl-ipython3"><pre><span></span><span class="n">Y_train</span> <span class="o">=</span> <span class="n">to_categorical</span><span class="p">(</span><span class="n">y_train</span><span class="p">,</span> <span class="mi">10</span><span class="p">)</span>
  <span class="n">Y_test</span> <span class="o">=</span> <span class="n">to_categorical</span><span class="p">(</span><span class="n">y_test</span><span class="p">,</span> <span class="mi">10</span><span class="p">)</span>
  <span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Y Training matrix shape&quot;</span><span class="p">,</span> <span class="n">Y_train</span><span class="o">.</span><span class="n">shape</span><span class="p">)</span>
  <span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Y Testing matrix shape&quot;</span><span class="p">,</span> <span class="n">Y_test</span><span class="o">.</span><span class="n">shape</span><span class="p">)</span>
  </pre></div>

      </div>
  </div>
  </div>
  </div>

  <div class="jp-Cell-outputWrapper">


  <div class="jp-OutputArea jp-Cell-outputArea">

  <div class="jp-OutputArea-child">

      
      <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>


  <div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain">
  <pre>Y Training matrix shape (60000, 10)
  Y Testing matrix shape (10000, 10)
  </pre>
  </div>
  </div>

  </div>

  </div>

  </div>
  <div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
  </div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
  <p>정답 레이블 변환 (One-hot encoding)</p>
  <p>예를 들어 숫자 3이 정답이면 → [0,0,0,1,0,0,0,0,0,0] 이렇게 바꿔줌.</p>
  <p>10개 클래스(0~9 숫자) 중 하나로 표시.</p>

  </div>
  </div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
  <div class="jp-Cell-inputWrapper">
  <div class="jp-InputArea jp-Cell-inputArea">
  <div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[&nbsp;]:</div>
  <div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
      <div class="CodeMirror cm-s-jupyter">
  <div class=" highlight hl-ipython3"><pre><span></span><span class="n">model</span> <span class="o">=</span> <span class="n">Sequential</span><span class="p">()</span>
  <span class="n">model</span><span class="o">.</span><span class="n">add</span><span class="p">(</span><span class="n">Dense</span><span class="p">(</span><span class="mi">512</span><span class="p">,</span> <span class="n">input_shape</span><span class="o">=</span><span class="p">(</span><span class="mi">784</span><span class="p">,)))</span>
  <span class="n">model</span><span class="o">.</span><span class="n">add</span><span class="p">(</span><span class="n">Activation</span><span class="p">(</span><span class="s1">&#39;relu&#39;</span><span class="p">))</span>
  <span class="n">model</span><span class="o">.</span><span class="n">add</span><span class="p">(</span><span class="n">Dense</span><span class="p">(</span><span class="mi">256</span><span class="p">))</span>
  <span class="n">model</span><span class="o">.</span><span class="n">add</span><span class="p">(</span><span class="n">Activation</span><span class="p">(</span><span class="s1">&#39;relu&#39;</span><span class="p">))</span>
  <span class="n">model</span><span class="o">.</span><span class="n">add</span><span class="p">(</span><span class="n">Dense</span><span class="p">(</span><span class="mi">10</span><span class="p">))</span>
  <span class="n">model</span><span class="o">.</span><span class="n">add</span><span class="p">(</span><span class="n">Activation</span><span class="p">(</span><span class="s1">&#39;softmax&#39;</span><span class="p">))</span>
  <span class="n">model</span><span class="o">.</span><span class="n">summary</span><span class="p">()</span>
  </pre></div>

      </div>
  </div>
  </div>
  </div>

  <div class="jp-Cell-outputWrapper">


  <div class="jp-OutputArea jp-Cell-outputArea">

  <div class="jp-OutputArea-child">

      
      <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>


  <div class="jp-RenderedText jp-OutputArea-output" data-mime-type="application/vnd.jupyter.stderr">
  <pre>/usr/local/lib/python3.11/dist-packages/keras/src/layers/core/dense.py:87: UserWarning: Do not pass an `input_shape`/`input_dim` argument to a layer. When using Sequential models, prefer using an `Input(shape)` object as the first layer in the model instead.
    super().__init__(activity_regularizer=activity_regularizer, **kwargs)
  </pre>
  </div>
  </div>

  <div class="jp-OutputArea-child">

      
      <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>



  <div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output " data-mime-type="text/html">
  <pre style="white-space:pre;overflow-x:auto;line-height:normal;font-family:Menlo,'DejaVu Sans Mono',consolas,'Courier New',monospace"><span style="font-weight: bold">Model: "sequential"</span>
  </pre>

  </div>

  </div>

  <div class="jp-OutputArea-child">

      
      <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>



  <div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output " data-mime-type="text/html">
  <pre style="white-space:pre;overflow-x:auto;line-height:normal;font-family:Menlo,'DejaVu Sans Mono',consolas,'Courier New',monospace">┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━┓
  ┃<span style="font-weight: bold"> Layer (type)                    </span>┃<span style="font-weight: bold"> Output Shape           </span>┃<span style="font-weight: bold">       Param # </span>┃
  ┡━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━┩
  │ dense (<span style="color: #0087ff; text-decoration-color: #0087ff">Dense</span>)                   │ (<span style="color: #00d7ff; text-decoration-color: #00d7ff">None</span>, <span style="color: #00af00; text-decoration-color: #00af00">512</span>)            │       <span style="color: #00af00; text-decoration-color: #00af00">401,920</span> │
  ├─────────────────────────────────┼────────────────────────┼───────────────┤
  │ activation (<span style="color: #0087ff; text-decoration-color: #0087ff">Activation</span>)         │ (<span style="color: #00d7ff; text-decoration-color: #00d7ff">None</span>, <span style="color: #00af00; text-decoration-color: #00af00">512</span>)            │             <span style="color: #00af00; text-decoration-color: #00af00">0</span> │
  ├─────────────────────────────────┼────────────────────────┼───────────────┤
  │ dense_1 (<span style="color: #0087ff; text-decoration-color: #0087ff">Dense</span>)                 │ (<span style="color: #00d7ff; text-decoration-color: #00d7ff">None</span>, <span style="color: #00af00; text-decoration-color: #00af00">256</span>)            │       <span style="color: #00af00; text-decoration-color: #00af00">131,328</span> │
  ├─────────────────────────────────┼────────────────────────┼───────────────┤
  │ activation_1 (<span style="color: #0087ff; text-decoration-color: #0087ff">Activation</span>)       │ (<span style="color: #00d7ff; text-decoration-color: #00d7ff">None</span>, <span style="color: #00af00; text-decoration-color: #00af00">256</span>)            │             <span style="color: #00af00; text-decoration-color: #00af00">0</span> │
  ├─────────────────────────────────┼────────────────────────┼───────────────┤
  │ dense_2 (<span style="color: #0087ff; text-decoration-color: #0087ff">Dense</span>)                 │ (<span style="color: #00d7ff; text-decoration-color: #00d7ff">None</span>, <span style="color: #00af00; text-decoration-color: #00af00">10</span>)             │         <span style="color: #00af00; text-decoration-color: #00af00">2,570</span> │
  ├─────────────────────────────────┼────────────────────────┼───────────────┤
  │ activation_2 (<span style="color: #0087ff; text-decoration-color: #0087ff">Activation</span>)       │ (<span style="color: #00d7ff; text-decoration-color: #00d7ff">None</span>, <span style="color: #00af00; text-decoration-color: #00af00">10</span>)             │             <span style="color: #00af00; text-decoration-color: #00af00">0</span> │
  └─────────────────────────────────┴────────────────────────┴───────────────┘
  </pre>

  </div>

  </div>

  <div class="jp-OutputArea-child">

      
      <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>



  <div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output " data-mime-type="text/html">
  <pre style="white-space:pre;overflow-x:auto;line-height:normal;font-family:Menlo,'DejaVu Sans Mono',consolas,'Courier New',monospace"><span style="font-weight: bold"> Total params: </span><span style="color: #00af00; text-decoration-color: #00af00">535,818</span> (2.04 MB)
  </pre>

  </div>

  </div>

  <div class="jp-OutputArea-child">

      
      <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>



  <div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output " data-mime-type="text/html">
  <pre style="white-space:pre;overflow-x:auto;line-height:normal;font-family:Menlo,'DejaVu Sans Mono',consolas,'Courier New',monospace"><span style="font-weight: bold"> Trainable params: </span><span style="color: #00af00; text-decoration-color: #00af00">535,818</span> (2.04 MB)
  </pre>

  </div>

  </div>

  <div class="jp-OutputArea-child">

      
      <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>



  <div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output " data-mime-type="text/html">
  <pre style="white-space:pre;overflow-x:auto;line-height:normal;font-family:Menlo,'DejaVu Sans Mono',consolas,'Courier New',monospace"><span style="font-weight: bold"> Non-trainable params: </span><span style="color: #00af00; text-decoration-color: #00af00">0</span> (0.00 B)
  </pre>

  </div>

  </div>

  </div>

  </div>

  </div>
  <div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
  </div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
  <p>모델 만들기</p>
  <p>Sequential 모델: 층을 하나씩 순서대로 쌓아 올리는 방식.</p>
  <p>Dense 층: 완전히 연결된 층 (모든 뉴런이 앞뒤 층 뉴런과 연결).</p>
  <p>relu: 활성화 함수 (0 이하는 버리고, 0 초과는 그대로 통과시킴).</p>
  <p>softmax: 최종 결과를 10개 클래스 확률로 출력 (가장 높은 확률을 정답으로 예측).</p>
  <p>구조 요약:</p>
  <p>입력: 784개</p>
  <p>첫 번째 은닉층: 512개 뉴런 (ReLU)</p>
  <p>두 번째 은닉층: 256개 뉴런 (ReLU)</p>
  <p>출력층: 10개 뉴런 (Softmax)</p>

  </div>
  </div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
  <div class="jp-Cell-inputWrapper">
  <div class="jp-InputArea jp-Cell-inputArea">
  <div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[&nbsp;]:</div>
  <div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
      <div class="CodeMirror cm-s-jupyter">
  <div class=" highlight hl-ipython3"><pre><span></span><span class="n">model</span><span class="o">.</span><span class="n">compile</span><span class="p">(</span><span class="n">loss</span><span class="o">=</span><span class="s1">&#39;categorical_crossentropy&#39;</span><span class="p">,</span> <span class="n">optimizer</span><span class="o">=</span><span class="s1">&#39;adam&#39;</span><span class="p">,</span> <span class="n">metrics</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;accuracy&#39;</span><span class="p">])</span>
  <span class="n">model</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">X_train</span><span class="p">,</span> <span class="n">Y_train</span><span class="p">,</span> <span class="n">batch_size</span><span class="o">=</span><span class="mi">128</span><span class="p">,</span> <span class="n">epochs</span><span class="o">=</span><span class="mi">10</span><span class="p">,</span> <span class="n">verbose</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span>
  </pre></div>

      </div>
  </div>
  </div>
  </div>

  <div class="jp-Cell-outputWrapper">


  <div class="jp-OutputArea jp-Cell-outputArea">

  <div class="jp-OutputArea-child">

      
      <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>


  <div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain">
  <pre>Epoch 1/10
  <span class="ansi-bold">469/469</span> <span class="ansi-green-fg">━━━━━━━━━━━━━━━━━━━━</span> <span class="ansi-bold">9s</span> 15ms/step - accuracy: 0.8820 - loss: 0.4068
  Epoch 2/10
  <span class="ansi-bold">469/469</span> <span class="ansi-green-fg">━━━━━━━━━━━━━━━━━━━━</span> <span class="ansi-bold">10s</span> 15ms/step - accuracy: 0.9740 - loss: 0.0841
  Epoch 3/10
  <span class="ansi-bold">469/469</span> <span class="ansi-green-fg">━━━━━━━━━━━━━━━━━━━━</span> <span class="ansi-bold">10s</span> 15ms/step - accuracy: 0.9852 - loss: 0.0472
  Epoch 4/10
  <span class="ansi-bold">469/469</span> <span class="ansi-green-fg">━━━━━━━━━━━━━━━━━━━━</span> <span class="ansi-bold">9s</span> 13ms/step - accuracy: 0.9890 - loss: 0.0345
  Epoch 5/10
  <span class="ansi-bold">469/469</span> <span class="ansi-green-fg">━━━━━━━━━━━━━━━━━━━━</span> <span class="ansi-bold">10s</span> 13ms/step - accuracy: 0.9922 - loss: 0.0238
  Epoch 6/10
  <span class="ansi-bold">469/469</span> <span class="ansi-green-fg">━━━━━━━━━━━━━━━━━━━━</span> <span class="ansi-bold">7s</span> 15ms/step - accuracy: 0.9945 - loss: 0.0184
  Epoch 7/10
  <span class="ansi-bold">469/469</span> <span class="ansi-green-fg">━━━━━━━━━━━━━━━━━━━━</span> <span class="ansi-bold">10s</span> 14ms/step - accuracy: 0.9943 - loss: 0.0178
  Epoch 8/10
  <span class="ansi-bold">469/469</span> <span class="ansi-green-fg">━━━━━━━━━━━━━━━━━━━━</span> <span class="ansi-bold">10s</span> 13ms/step - accuracy: 0.9951 - loss: 0.0150
  Epoch 9/10
  <span class="ansi-bold">469/469</span> <span class="ansi-green-fg">━━━━━━━━━━━━━━━━━━━━</span> <span class="ansi-bold">10s</span> 13ms/step - accuracy: 0.9953 - loss: 0.0130
  Epoch 10/10
  <span class="ansi-bold">469/469</span> <span class="ansi-green-fg">━━━━━━━━━━━━━━━━━━━━</span> <span class="ansi-bold">7s</span> 15ms/step - accuracy: 0.9953 - loss: 0.0142
  </pre>
  </div>
  </div>

  <div class="jp-OutputArea-child">

      
      <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[&nbsp;]:</div>




  <div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain">
  <pre>&lt;keras.src.callbacks.history.History at 0x7bf85441c7d0&gt;</pre>
  </div>

  </div>

  </div>

  </div>

  </div>
  <div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
  </div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
  <p>모델 컴파일 (학습 준비)</p>
  <p>loss: 정답과 예측 차이를 계산하는 방법 (여기선 다중 분류니까 categorical_crossentropy 사용).</p>
  <p>optimizer: 모델을 업데이트하는 방법 (여기선 adam이라는 똑똑한 최적화 알고리즘 사용).</p>
  <p>metrics: 평가 기준 (여기선 정확도 accuracy).</p>
  <p>모델 훈련</p>
  <p>batch_size=128: 128개씩 끊어서 한 번에 학습.</p>
  <p>epochs=10: 데이터 전체를 10번 반복해서 학습.</p>
  <p>verbose=1: 학습 과정 출력.</p>

  </div>
  </div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
  <div class="jp-Cell-inputWrapper">
  <div class="jp-InputArea jp-Cell-inputArea">
  <div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[&nbsp;]:</div>
  <div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
      <div class="CodeMirror cm-s-jupyter">
  <div class=" highlight hl-ipython3"><pre><span></span><span class="n">score</span> <span class="o">=</span> <span class="n">model</span><span class="o">.</span><span class="n">evaluate</span><span class="p">(</span><span class="n">X_test</span><span class="p">,</span> <span class="n">Y_test</span><span class="p">)</span>
  <span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Test lose:&#39;</span><span class="p">,</span> <span class="n">score</span><span class="p">[</span><span class="mi">0</span><span class="p">])</span>
  <span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Test accuracy:&#39;</span><span class="p">,</span> <span class="n">score</span><span class="p">[</span><span class="mi">1</span><span class="p">])</span>
  </pre></div>

      </div>
  </div>
  </div>
  </div>

  <div class="jp-Cell-outputWrapper">


  <div class="jp-OutputArea jp-Cell-outputArea">

  <div class="jp-OutputArea-child">

      
      <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>


  <div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain">
  <pre><span class="ansi-bold">313/313</span> <span class="ansi-green-fg">━━━━━━━━━━━━━━━━━━━━</span> <span class="ansi-bold">2s</span> 5ms/step - accuracy: 0.9774 - loss: 0.0906
  Test lose: 0.07323487848043442
  Test accuracy: 0.9815999865531921
  </pre>
  </div>
  </div>

  </div>

  </div>

  </div>
  <div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
  </div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
  <p>모델 평가</p>
  <p>테스트 데이터로 모델을 평가하고, 손실(loss)과 정확도(accuracy)를 출력.</p>

  </div>
  </div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
  <div class="jp-Cell-inputWrapper">
  <div class="jp-InputArea jp-Cell-inputArea">
  <div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[&nbsp;]:</div>
  <div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
      <div class="CodeMirror cm-s-jupyter">
  <div class=" highlight hl-ipython3"><pre><span></span><span class="n">predicted_classes</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">argmax</span><span class="p">(</span><span class="n">model</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">X_test</span><span class="p">),</span> <span class="n">axis</span><span class="o">=-</span><span class="mi">1</span><span class="p">)</span>
  <span class="n">correct_indices</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">nonzero</span><span class="p">(</span><span class="n">predicted_classes</span> <span class="o">==</span> <span class="n">y_test</span><span class="p">)[</span><span class="mi">0</span><span class="p">]</span>
  <span class="n">incorrect_indices</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">nonzero</span><span class="p">(</span><span class="n">predicted_classes</span> <span class="o">!=</span> <span class="n">y_test</span><span class="p">)[</span><span class="mi">0</span><span class="p">]</span>
  </pre></div>

      </div>
  </div>
  </div>
  </div>

  <div class="jp-Cell-outputWrapper">


  <div class="jp-OutputArea jp-Cell-outputArea">

  <div class="jp-OutputArea-child">

      
      <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>


  <div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain">
  <pre><span class="ansi-bold">313/313</span> <span class="ansi-green-fg">━━━━━━━━━━━━━━━━━━━━</span> <span class="ansi-bold">1s</span> 3ms/step
  </pre>
  </div>
  </div>

  </div>

  </div>

  </div>
  <div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
  </div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
  <p>예측 결과 보기</p>
  <p>모델 예측값과 실제 정답을 비교해서</p>
  <p>맞춘 것과 틀린 것의 인덱스를 따로 저장</p>

  </div>
  </div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
  <div class="jp-Cell-inputWrapper">
  <div class="jp-InputArea jp-Cell-inputArea">
  <div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[&nbsp;]:</div>
  <div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
      <div class="CodeMirror cm-s-jupyter">
  <div class=" highlight hl-ipython3"><pre><span></span><span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">()</span>
  <span class="k">for</span> <span class="n">i</span><span class="p">,</span> <span class="n">correct</span> <span class="ow">in</span> <span class="nb">enumerate</span><span class="p">(</span><span class="n">correct_indices</span><span class="p">[:</span><span class="mi">9</span><span class="p">]):</span>
      <span class="n">plt</span><span class="o">.</span><span class="n">subplot</span><span class="p">(</span><span class="mi">3</span><span class="p">,</span><span class="mi">3</span><span class="p">,</span><span class="n">i</span><span class="o">+</span><span class="mi">1</span><span class="p">)</span>
      <span class="n">plt</span><span class="o">.</span><span class="n">imshow</span><span class="p">(</span><span class="n">X_test</span><span class="p">[</span><span class="n">correct</span><span class="p">]</span><span class="o">.</span><span class="n">reshape</span><span class="p">(</span><span class="mi">28</span><span class="p">,</span><span class="mi">28</span><span class="p">),</span> <span class="n">cmap</span><span class="o">=</span><span class="s1">&#39;gray&#39;</span><span class="p">,</span> <span class="n">interpolation</span><span class="o">=</span><span class="s1">&#39;none&#39;</span><span class="p">)</span>
      <span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s2">&quot;Predicted </span><span class="si">{}</span><span class="s2">, Class </span><span class="si">{}</span><span class="s2">&quot;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">predicted_classes</span><span class="p">[</span><span class="n">correct</span><span class="p">],</span> <span class="n">y_test</span><span class="p">[</span><span class="n">correct</span><span class="p">]))</span>
  </pre></div>

      </div>
  </div>
  </div>
  </div>

  <div class="jp-Cell-outputWrapper">


  <div class="jp-OutputArea jp-Cell-outputArea">

  <div class="jp-OutputArea-child">

      
      <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>




  <div class="jp-RenderedImage jp-OutputArea-output ">
  <img src="data:image/png;base64,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
  "
  >
  </div>

  </div>

  </div>

  </div>

  </div>
  <div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
  </div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
  <p>맞춘 그림 보여주기</p>
  <p>맞게 예측한 9개 그림을 3x3 격자로 표시.</p>
  <p>"예측값 / 실제 정답"도 같이 제목으로 보여줌</p>

  </div>
  </div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
  <div class="jp-Cell-inputWrapper">
  <div class="jp-InputArea jp-Cell-inputArea">
  <div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[&nbsp;]:</div>
  <div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
      <div class="CodeMirror cm-s-jupyter">
  <div class=" highlight hl-ipython3"><pre><span></span><span class="n">plt</span><span class="o">.</span><span class="n">tight_layout</span><span class="p">()</span>
  </pre></div>

      </div>
  </div>
  </div>
  </div>

  <div class="jp-Cell-outputWrapper">


  <div class="jp-OutputArea jp-Cell-outputArea">

  <div class="jp-OutputArea-child">

      
      <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>




  <div class="jp-RenderedText jp-OutputArea-output " data-mime-type="text/plain">
  <pre>&lt;Figure size 640x480 with 0 Axes&gt;</pre>
  </div>

  </div>

  </div>

  </div>

  </div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
  <div class="jp-Cell-inputWrapper">
  <div class="jp-InputArea jp-Cell-inputArea">
  <div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[&nbsp;]:</div>
  <div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
      <div class="CodeMirror cm-s-jupyter">
  <div class=" highlight hl-ipython3"><pre><span></span><span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">()</span>
  <span class="k">for</span> <span class="n">i</span><span class="p">,</span> <span class="n">incorrect</span> <span class="ow">in</span> <span class="nb">enumerate</span><span class="p">(</span><span class="n">incorrect_indices</span><span class="p">[:</span><span class="mi">9</span><span class="p">]):</span>
      <span class="n">plt</span><span class="o">.</span><span class="n">subplot</span><span class="p">(</span><span class="mi">3</span><span class="p">,</span><span class="mi">3</span><span class="p">,</span><span class="n">i</span><span class="o">+</span><span class="mi">1</span><span class="p">)</span>
      <span class="n">plt</span><span class="o">.</span><span class="n">imshow</span><span class="p">(</span><span class="n">X_test</span><span class="p">[</span><span class="n">incorrect</span><span class="p">]</span><span class="o">.</span><span class="n">reshape</span><span class="p">(</span><span class="mi">28</span><span class="p">,</span><span class="mi">28</span><span class="p">),</span> <span class="n">cmap</span><span class="o">=</span><span class="s1">&#39;gray&#39;</span><span class="p">,</span> <span class="n">interpolation</span><span class="o">=</span><span class="s1">&#39;none&#39;</span><span class="p">)</span>
      <span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s2">&quot;Predicted </span><span class="si">{}</span><span class="s2">, Class </span><span class="si">{}</span><span class="s2">&quot;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">predicted_classes</span><span class="p">[</span><span class="n">incorrect</span><span class="p">],</span> <span class="n">y_test</span><span class="p">[</span><span class="n">incorrect</span><span class="p">]))</span>
  </pre></div>

      </div>
  </div>
  </div>
  </div>

  <div class="jp-Cell-outputWrapper">


  <div class="jp-OutputArea jp-Cell-outputArea">

  <div class="jp-OutputArea-child">

      
      <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>




  <div class="jp-RenderedImage jp-OutputArea-output ">
  <img src="data:image/png;base64,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96VuoKtXr+L06dOoXr06/Pz8EBERgTlz5qBOnTr6y558fHzQs2dPNfMmMhlrl6wVa5esickNi+PHj6Njx476eNy4cQCAgQMHYtWqVZg4cSIePHiAYcOGITU1FW3btsW2bdssah4APz8/g6///PPPpZQJlabyULumUl6frxz5v2DBAin+448/jN63ra2tFH/44YcG11d21XNMhfGssXb//PNPKb57964UOzg4SPG5c+dKPKfCLFu2TIr79esnxVWrVi3FbKyfyQ2LDh06GLx5kEajwaxZszBr1qxiJUakNtYuWSvWLlkT3iuEiIiIVMOGBREREanGIuaxICJ1PPPMM1I8ePBgKd66dasUf/rpp2YfSzle46233jK4/ubNm80+Flm/uXPnSvGSJUuk+NVXX5XiefPmlXhOua5evSrFjx49kmLlGIvKlSsbjLOystRLzgqxx4KIiIhUw4YFERERqaZCngpR3s55yJAhBmPlXf9OnjwpxQcOHJDiF154QYrbtm2rf16vXj3ptQ4dOhSdsAFr1qyR4gsXLkhxTExMsfZP1qV79+5SrJyyWXlr8+J47bXXTFo/OjpatWOT9Tly5IgUK39Xlaft7ty5I8X//e9/VctF+bs7adIkKfb29ja4ffv27aW4Xbt2UhwXF2d+cuUAeyyIiIhINWxYEBERkWrYsCAiIiLVaISh6dzKSFpaGlxdXUts/8p9Hzp0SIqVt3dWyszMlGLl7X6Vt2UvyfeilJSUJMWBgYFSfPPmzRI7tk6ng4uLS4nt3xqUdO0WpUGDBlL822+/SbHysjjlGJyPPvpIio8fP65/rryU9dSpU1KsvE32V199JcXDhw+X4pycHFgK1m7p165yfNibb75pcP0bN25I8WeffWb2sZV1rqzFr7/+WoqV4z+CgoKkePv27VLcp08fKd60aZM5aRrN0uqXPRZERESkGjYsiIiISDVsWBAREZFqKuQYC6V//etfUvz+++9LsSm3kjbV559/LsWmfh3vvPOOFCvPYyvnzbh06ZJJ+zeFpZ3nKwtlPcZCSVnLs2fPlmKNRiPFqampUnzs2DH989atW0uvKcdUZGdnS7Gvr68UJycnF51wGWHtln7t2traSrFy/h/l+B8PDw/Vjq2ci2jRokUGj52eni7FyrFKM2fOlGLlfDFTpkwxK09jWVr9sseCiIiIVMOGBRER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
  "
  >
  </div>

  </div>

  </div>

  </div>

  </div>
  <div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
  </div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
  <p>틀린 그림 보여주기</p>
  <p>틀리게 예측한 9개 그림도 3x3 격자로 표시.</p>

  </div>
  </div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
  <div class="jp-Cell-inputWrapper">
  <div class="jp-InputArea jp-Cell-inputArea">
  <div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[&nbsp;]:</div>
  <div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
      <div class="CodeMirror cm-s-jupyter">
  <div class=" highlight hl-ipython3"><pre><span></span><span class="n">plt</span><span class="o">.</span><span class="n">tight_layout</span><span class="p">()</span>
  </pre></div>

      </div>
  </div>
  </div>
  </div>

  <div class="jp-Cell-outputWrapper">


  <div class="jp-OutputArea jp-Cell-outputArea">

  <div class="jp-OutputArea-child">

      
      <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>




  <div class="jp-RenderedText jp-OutputArea-output " data-mime-type="text/plain">
  <pre>&lt;Figure size 640x480 with 0 Axes&gt;</pre>
  </div>

  </div>

  </div>

  </div>

  </div>
  </body>







  </html>

</p>
