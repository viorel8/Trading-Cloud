
<h2 align="center"> Trading Cloud Indicators and Tools  </h2>

<p align="center">
  <img  width="900" src="doc/assets/pine_script_logo.webp" alt=" Trading Cloud Indicators and Tools" >
</p>
<p align="center" > The site contains indicators created by Jo Pepin and Vio. The code is intendes as a common framework for testing and developing TradingView Pinescript Indicators. </p>

<h5 align="center" >

  <a href="./doc/jo-pippin/monday_script_v1.md" >monday_script_v1</a></br>
  
</br>

![Idnetity server with BFF flow](./doc/jo-pippin/monday_script_v1.md "Indicator general description")
doc/jo-pippin/monday_script_v1.md

<div style="width: 100%; display: flex; justify-content: center; z-index: 3; flex-shrink: 0;">
    <div style="max-width: 100%; min-width: 0px; width: 100%;">
        <div
            style="width: 100%; display: flex; flex-direction: column; align-items: center; flex-shrink: 0; flex-grow: 0;">
            <div style="max-width: 100%; padding-left: calc(48px + env(safe-area-inset-left)); width: 100%;">
                <div contenteditable="false" class="pseudoSelection" data-content-editable-void="true"
                    style="user-select: none; --pseudoSelection--background:transparent; pointer-events: none;">
                    <div class="notion-page-controls"
                        style="display: flex; justify-content: flex-start; flex-wrap: wrap; margin-top: 4px; margin-bottom: 4px; margin-left: -1px; color: rgba(55, 53, 47, 0.5); font-family: ui-sans-serif, -apple-system, BlinkMacSystemFont, &quot;Segoe UI&quot;, Helvetica, &quot;Apple Color Emoji&quot;, Arial, sans-serif, &quot;Segoe UI Emoji&quot;, &quot;Segoe UI Symbol&quot;; height: 24px; pointer-events: auto;">
                    </div>
                </div>
                <div style="padding-right: calc(48px + env(safe-area-inset-right));">
                    <div style="display: flex; align-items: flex-start;">
                        <div class="notion-record-icon notranslate"
                            style="display: flex; align-items: center; justify-content: center; height: 36px; width: 36px; border-radius: 0.25em; flex-shrink: 0; position: relative; z-index: 1; margin: 4px 8px 0px 3px; pointer-events: auto;">
                            <div>
                                <div style="width: 100%; height: 100%;"><img src="/icons/aquarius_gray.svg?mode=light"
                                        referrerpolicy="same-origin"
                                        style="display: block; object-fit: cover; border-radius: 3px; width: 39.6px; height: 39.6px; transition: opacity 100ms ease-out 0s;">
                                </div>
                            </div>
                        </div>
                        <div style="flex: 1 1 0%;">
                            <div data-block-id="29ec6a24-ffba-48a9-833f-9ac8833cfa92"
                                class="notion-selectable notion-page-block"
                                style="color: rgb(55, 53, 47); font-weight: 700; line-height: 1.2; font-size: 32px; font-family: ui-sans-serif, -apple-system, BlinkMacSystemFont, &quot;Segoe UI&quot;, Helvetica, &quot;Apple Color Emoji&quot;, Arial, sans-serif, &quot;Segoe UI Emoji&quot;, &quot;Segoe UI Symbol&quot;; cursor: text; display: flex; align-items: center;">
                                <div spellcheck="true" placeholder="Untitled" data-content-editable-leaf="true"
                                    contenteditable="false"
                                    style="max-width: 100%; width: 100%; white-space: pre-wrap; word-break: break-word; caret-color: rgb(55, 53, 47); padding: 3px 2px;">
                                    Monday Script (ONLY CRYPTO) V1 No vol or OI | Runs fast </div>
                            </div>
                            <div style="margin-left: 4px;"></div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div
            style="width: 100%; display: flex; flex-direction: column; align-items: center; flex-shrink: 0; flex-grow: 0;">
            <div contenteditable="false" data-content-editable-void="true"
                style="padding-left: calc(48px + env(safe-area-inset-left)); padding-right: calc(48px + env(safe-area-inset-right)); max-width: 100%; width: 100%;">
                <div style="width: 100%; font-size: 14px;">
                    <div style="width: 100%; max-width: 100%; padding: 8px 0px; margin: 0px auto;">
                        <div style="margin: 0px;">
                            <div>
                                <div style="display: flex; padding-bottom: 4px; width: 100%;">
                                    <div
                                        style="display: flex; align-items: center; height: 34px; width: 160px; flex: 0 0 auto; color: rgba(55, 53, 47, 0.65);">
                                        <div class="notion-focusable" role="button" aria-disabled="true" tabindex="-1"
                                            style="user-select: none; transition: background 20ms ease-in 0s; display: flex; align-items: center; height: 100%; width: 100%; border-radius: 3px; padding: 0px 6px;">
                                            <div
                                                style="display: flex; align-items: center; line-height: 120%; font-size: 14px; min-width: 0px;">
                                                <div style="margin-right: 8px;"><svg viewBox="0 0 16 16"
                                                        class="typesMultipleSelect"
                                                        style="width: 18px; height: 18px; display: block; fill: rgba(55, 53, 47, 0.45); flex-shrink: 0; backface-visibility: hidden;">
                                                        <path
                                                            d="M1.91602 4.83789C2.44238 4.83789 2.87305 4.40723 2.87305 3.87402C2.87305 3.34766 2.44238 2.91699 1.91602 2.91699C1.38281 2.91699 0.952148 3.34766 0.952148 3.87402C0.952148 4.40723 1.38281 4.83789 1.91602 4.83789ZM5.1084 4.52344H14.3984C14.7607 4.52344 15.0479 4.23633 15.0479 3.87402C15.0479 3.51172 14.7607 3.22461 14.3984 3.22461H5.1084C4.74609 3.22461 4.45898 3.51172 4.45898 3.87402C4.45898 4.23633 4.74609 4.52344 5.1084 4.52344ZM1.91602 9.03516C2.44238 9.03516 2.87305 8.60449 2.87305 8.07129C2.87305 7.54492 2.44238 7.11426 1.91602 7.11426C1.38281 7.11426 0.952148 7.54492 0.952148 8.07129C0.952148 8.60449 1.38281 9.03516 1.91602 9.03516ZM5.1084 8.7207H14.3984C14.7607 8.7207 15.0479 8.43359 15.0479 8.07129C15.0479 7.70898 14.7607 7.42188 14.3984 7.42188H5.1084C4.74609 7.42188 4.45898 7.70898 4.45898 8.07129C4.45898 8.43359 4.74609 8.7207 5.1084 8.7207ZM1.91602 13.2324C2.44238 13.2324 2.87305 12.8018 2.87305 12.2686C2.87305 11.7422 2.44238 11.3115 1.91602 11.3115C1.38281 11.3115 0.952148 11.7422 0.952148 12.2686C0.952148 12.8018 1.38281 13.2324 1.91602 13.2324ZM5.1084 12.918H14.3984C14.7607 12.918 15.0479 12.6309 15.0479 12.2686C15.0479 11.9062 14.7607 11.6191 14.3984 11.6191H5.1084C4.74609 11.6191 4.45898 11.9062 4.45898 12.2686C4.45898 12.6309 4.74609 12.918 5.1084 12.918Z">
                                                        </path>
                                                    </svg></div>
                                                <div
                                                    style="white-space: nowrap; overflow: hidden; text-overflow: ellipsis;">
                                                    Language</div>
                                            </div>
                                        </div>
                                    </div>
                                    <div
                                        style="display: flex; margin-left: 4px; height: 100%; flex: 1 1 auto; flex-direction: column; min-width: 0px;">
                                        <div
                                            style="display: flex; align-items: center; margin-left: 4px; height: 100%; flex: 1 1 auto; min-width: 0px;">
                                            <div class="notion-focusable" role="button" aria-disabled="true"
                                                tabindex="-1"
                                                style="user-select: none; transition: background 20ms ease-in 0s; display: flex; align-items: center; border-radius: 3px; width: 100%; min-height: 34px; padding: 0px 8px; font-size: 14px; overflow: hidden;">
                                                <div
                                                    style="display: flex; flex-wrap: wrap; padding-top: 8px; padding-bottom: 2px;">
                                                    <div
                                                        style="display: flex; align-items: center; flex-shrink: 1; min-width: 0px; height: 20px; border-radius: 3px; padding-left: 6px; padding-right: 6px; font-size: 14px; line-height: 120%; color: rgb(50, 48, 44); background: rgba(227, 226, 224, 0.5); margin: 0px 6px 6px 0px;">
                                                        <div
                                                            style="white-space: nowrap; overflow: hidden; text-overflow: ellipsis; display: flex; align-items: center;">
                                                            <div style="display: block;">PineScript</div>
                                                        </div>
                                                    </div>
                                                </div>
                                                <div style="display: flex; position: absolute; right: 6px; top: 4px;">
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                            <div>
                                <div style="display: flex; padding-bottom: 4px; width: 100%;">
                                    <div
                                        style="display: flex; align-items: center; height: 34px; width: 160px; flex: 0 0 auto; color: rgba(55, 53, 47, 0.65);">
                                        <div class="notion-focusable" role="button" aria-disabled="true" tabindex="-1"
                                            style="user-select: none; transition: background 20ms ease-in 0s; display: flex; align-items: center; height: 100%; width: 100%; border-radius: 3px; padding: 0px 6px;">
                                            <div
                                                style="display: flex; align-items: center; line-height: 120%; font-size: 14px; min-width: 0px;">
                                                <div style="margin-right: 8px;"><svg viewBox="0 0 16 16"
                                                        class="typesCreatedAt"
                                                        style="width: 18px; height: 18px; display: block; fill: rgba(55, 53, 47, 0.45); flex-shrink: 0; backface-visibility: hidden;">
                                                        <path
                                                            d="M8 15.126C11.8623 15.126 15.0615 11.9336 15.0615 8.06445C15.0615 4.20215 11.8623 1.00293 7.99316 1.00293C4.13086 1.00293 0.938477 4.20215 0.938477 8.06445C0.938477 11.9336 4.1377 15.126 8 15.126ZM8 13.7383C4.85547 13.7383 2.33301 11.209 2.33301 8.06445C2.33301 4.91992 4.84863 2.39746 7.99316 2.39746C11.1377 2.39746 13.6738 4.91992 13.6738 8.06445C13.6738 11.209 11.1445 13.7383 8 13.7383ZM4.54102 8.91211H7.99316C8.30078 8.91211 8.54004 8.67285 8.54004 8.37207V3.8877C8.54004 3.58691 8.30078 3.34766 7.99316 3.34766C7.69238 3.34766 7.45312 3.58691 7.45312 3.8877V7.83203H4.54102C4.2334 7.83203 4.00098 8.06445 4.00098 8.37207C4.00098 8.67285 4.2334 8.91211 4.54102 8.91211Z">
                                                        </path>
                                                    </svg></div>
                                                <div
                                                    style="white-space: nowrap; overflow: hidden; text-overflow: ellipsis;">
                                                    Last Edited</div>
                                            </div>
                                        </div>
                                    </div>
                                    <div
                                        style="display: flex; margin-left: 4px; height: 100%; flex: 1 1 auto; flex-direction: column; min-width: 0px;">
                                        <div
                                            style="display: flex; align-items: center; margin-left: 4px; height: 100%; flex: 1 1 auto; min-width: 0px;">
                                            <div
                                                style="display: flex; align-items: center; border-radius: 3px; width: 100%; min-height: 34px; padding: 6px 8px 7px; font-size: 14px; overflow: hidden;">
                                                <div
                                                    style="line-height: 1.5; word-break: break-word; white-space: pre-wrap; pointer-events: none;">
                                                    February 9, 2023 10:22 AM</div>
                                                <div style="display: flex; position: absolute; right: 6px; top: 4px;">
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                            <div>
                                <div style="display: flex; padding-bottom: 4px; width: 100%;">
                                    <div
                                        style="display: flex; align-items: center; height: 34px; width: 160px; flex: 0 0 auto; color: rgba(55, 53, 47, 0.65);">
                                        <div class="notion-focusable" role="button" aria-disabled="true" tabindex="-1"
                                            style="user-select: none; transition: background 20ms ease-in 0s; display: flex; align-items: center; height: 100%; width: 100%; border-radius: 3px; padding: 0px 6px;">
                                            <div
                                                style="display: flex; align-items: center; line-height: 120%; font-size: 14px; min-width: 0px;">
                                                <div style="margin-right: 8px;"><svg viewBox="0 0 16 16"
                                                        class="typesStatus"
                                                        style="width: 18px; height: 18px; display: block; fill: rgba(55, 53, 47, 0.45); flex-shrink: 0; backface-visibility: hidden;">
                                                        <path
                                                            d="M8.75488 1.02344C8.75488 0.613281 8.41309 0.264648 8.00293 0.264648C7.59277 0.264648 7.25098 0.613281 7.25098 1.02344V3.11523C7.25098 3.51855 7.59277 3.86719 8.00293 3.86719C8.41309 3.86719 8.75488 3.51855 8.75488 3.11523V1.02344ZM3.91504 5.0293C4.20215 5.31641 4.69434 5.32324 4.97461 5.03613C5.26855 4.74902 5.26855 4.25684 4.98145 3.96973L3.53906 2.52051C3.25195 2.2334 2.7666 2.21973 2.47949 2.50684C2.19238 2.79395 2.18555 3.28613 2.47266 3.57324L3.91504 5.0293ZM10.9629 4.01758C10.6826 4.30469 10.6826 4.79688 10.9697 5.08398C11.2568 5.37109 11.749 5.36426 12.0361 5.07715L13.4854 3.62793C13.7725 3.34082 13.7725 2.84863 13.4785 2.55469C13.1982 2.27441 12.7061 2.27441 12.4189 2.56152L10.9629 4.01758ZM15.0234 8.78906C15.4336 8.78906 15.7822 8.44727 15.7822 8.03711C15.7822 7.62695 15.4336 7.28516 15.0234 7.28516H12.9385C12.5283 7.28516 12.1797 7.62695 12.1797 8.03711C12.1797 8.44727 12.5283 8.78906 12.9385 8.78906H15.0234ZM0.975586 7.28516C0.56543 7.28516 0.223633 7.62695 0.223633 8.03711C0.223633 8.44727 0.56543 8.78906 0.975586 8.78906H3.07422C3.48438 8.78906 3.83301 8.44727 3.83301 8.03711C3.83301 7.62695 3.48438 7.28516 3.07422 7.28516H0.975586ZM12.0361 10.9902C11.749 10.71 11.2568 10.71 10.9629 10.9971C10.6826 11.2842 10.6826 11.7764 10.9697 12.0635L12.4258 13.5127C12.7129 13.7998 13.2051 13.793 13.4922 13.5059C13.7793 13.2256 13.7725 12.7266 13.4854 12.4395L12.0361 10.9902ZM2.52051 12.4395C2.22656 12.7266 2.22656 13.2188 2.50684 13.5059C2.79395 13.793 3.28613 13.7998 3.57324 13.5127L5.02246 12.0703C5.31641 11.7832 5.31641 11.291 5.03613 11.0039C4.74902 10.7168 4.25684 10.71 3.96973 10.9971L2.52051 12.4395ZM8.75488 12.9658C8.75488 12.5557 8.41309 12.207 8.00293 12.207C7.59277 12.207 7.25098 12.5557 7.25098 12.9658V15.0576C7.25098 15.4609 7.59277 15.8096 8.00293 15.8096C8.41309 15.8096 8.75488 15.4609 8.75488 15.0576V12.9658Z">
                                                        </path>
                                                    </svg></div>
                                                <div
                                                    style="white-space: nowrap; overflow: hidden; text-overflow: ellipsis;">
                                                    Status</div>
                                            </div>
                                        </div>
                                    </div>
                                    <div
                                        style="display: flex; margin-left: 4px; height: 100%; flex: 1 1 auto; flex-direction: column; min-width: 0px;">
                                        <div
                                            style="display: flex; align-items: center; margin-left: 4px; height: 100%; flex: 1 1 auto; min-width: 0px;">
                                            <div class="notion-focusable" role="button" aria-disabled="true"
                                                tabindex="-1"
                                                style="user-select: none; transition: background 20ms ease-in 0s; display: flex; align-items: center; border-radius: 3px; width: 100%; min-height: 34px; padding: 0px 8px; font-size: 14px; overflow: hidden;">
                                                <div
                                                    style="display: flex; flex-wrap: wrap; padding-top: 8px; padding-bottom: 2px; flex-shrink: 0;">
                                                    <div
                                                        style="display: flex; align-items: center; flex-shrink: 0; min-width: 0px; height: 20px; border-radius: 10px; padding-left: 7px; padding-right: 9px; font-size: 14px; line-height: 120%; color: rgb(50, 48, 44); background: rgba(227, 226, 224, 0.5); margin: 0px 6px 6px 0px;">
                                                        <div
                                                            style="white-space: nowrap; overflow: hidden; text-overflow: ellipsis; display: flex; align-items: center;">
                                                            <div
                                                                style="margin-right: 5px; border-radius: 99px; height: 8px; width: 8px; background-color: rgb(145, 145, 142);">
                                                            </div>
                                                            <div style="display: block;">Not started</div>
                                                        </div>
                                                    </div>
                                                </div>
                                                <div style="display: flex; position: absolute; right: 6px; top: 4px;">
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                            <div>
                                <div style="display: flex; padding-bottom: 4px; width: 100%;">
                                    <div
                                        style="display: flex; align-items: center; height: 34px; width: 160px; flex: 0 0 auto; color: rgba(55, 53, 47, 0.65);">
                                        <div class="notion-focusable" role="button" aria-disabled="true" tabindex="-1"
                                            style="user-select: none; transition: background 20ms ease-in 0s; display: flex; align-items: center; height: 100%; width: 100%; border-radius: 3px; padding: 0px 6px;">
                                            <div
                                                style="display: flex; align-items: center; line-height: 120%; font-size: 14px; min-width: 0px;">
                                                <div style="margin-right: 8px;"><svg viewBox="0 0 16 16"
                                                        class="typesText"
                                                        style="width: 18px; height: 18px; display: block; fill: rgba(55, 53, 47, 0.45); flex-shrink: 0; backface-visibility: hidden;">
                                                        <path
                                                            d="M1.56738 3.25879H14.4258C14.7676 3.25879 15.0479 2.97852 15.0479 2.63672C15.0479 2.29492 14.7744 2.02148 14.4258 2.02148H1.56738C1.21875 2.02148 0.952148 2.29492 0.952148 2.63672C0.952148 2.97852 1.22559 3.25879 1.56738 3.25879ZM1.56738 6.84082H14.4258C14.7676 6.84082 15.0479 6.56055 15.0479 6.21875C15.0479 5.87695 14.7744 5.60352 14.4258 5.60352H1.56738C1.21875 5.60352 0.952148 5.87695 0.952148 6.21875C0.952148 6.56055 1.22559 6.84082 1.56738 6.84082ZM1.56738 10.4229H14.4258C14.7676 10.4229 15.0479 10.1426 15.0479 9.80078C15.0479 9.45898 14.7744 9.18555 14.4258 9.18555H1.56738C1.21875 9.18555 0.952148 9.45898 0.952148 9.80078C0.952148 10.1426 1.22559 10.4229 1.56738 10.4229ZM1.56738 14.0049H8.75879C9.10059 14.0049 9.38086 13.7246 9.38086 13.3828C9.38086 13.041 9.10742 12.7676 8.75879 12.7676H1.56738C1.21875 12.7676 0.952148 13.041 0.952148 13.3828C0.952148 13.7246 1.22559 14.0049 1.56738 14.0049Z">
                                                        </path>
                                                    </svg></div>
                                                <div
                                                    style="white-space: nowrap; overflow: hidden; text-overflow: ellipsis;">
                                                    Summary</div>
                                            </div>
                                        </div>
                                    </div>
                                    <div
                                        style="display: flex; margin-left: 4px; height: 100%; flex: 1 1 auto; flex-direction: column; min-width: 0px;">
                                        <div
                                            style="display: flex; align-items: center; margin-left: 4px; height: 100%; flex: 1 1 auto; min-width: 0px;">
                                            <div class="notion-focusable" role="button" aria-disabled="true"
                                                tabindex="-1"
                                                style="user-select: none; transition: background 20ms ease-in 0s; display: flex; align-items: center; border-radius: 3px; width: 100%; min-height: 34px; padding: 6px 8px 7px; font-size: 14px; overflow: hidden;">
                                                <span
                                                    style="line-height: 1.5; word-break: break-word; white-space: pre-wrap; pointer-events: none;">Locates
                                                    Mondays and extend through Tuesday. Shows Opening range and warning
                                                    when Monday H/L is breached on Tuesday </span>
                                                <div style="display: flex; position: absolute; right: 6px; top: 4px;">
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                            <div>
                                <div style="display: flex; padding-bottom: 4px; width: 100%;">
                                    <div
                                        style="display: flex; align-items: center; height: 34px; width: 160px; flex: 0 0 auto; color: rgba(55, 53, 47, 0.65);">
                                        <div class="notion-focusable" role="button" aria-disabled="true" tabindex="-1"
                                            style="user-select: none; transition: background 20ms ease-in 0s; display: flex; align-items: center; height: 100%; width: 100%; border-radius: 3px; padding: 0px 6px;">
                                            <div
                                                style="display: flex; align-items: center; line-height: 120%; font-size: 14px; min-width: 0px;">
                                                <div style="margin-right: 8px;"><svg viewBox="0 0 16 16"
                                                        class="typesText"
                                                        style="width: 18px; height: 18px; display: block; fill: rgba(55, 53, 47, 0.45); flex-shrink: 0; backface-visibility: hidden;">
                                                        <path
                                                            d="M1.56738 3.25879H14.4258C14.7676 3.25879 15.0479 2.97852 15.0479 2.63672C15.0479 2.29492 14.7744 2.02148 14.4258 2.02148H1.56738C1.21875 2.02148 0.952148 2.29492 0.952148 2.63672C0.952148 2.97852 1.22559 3.25879 1.56738 3.25879ZM1.56738 6.84082H14.4258C14.7676 6.84082 15.0479 6.56055 15.0479 6.21875C15.0479 5.87695 14.7744 5.60352 14.4258 5.60352H1.56738C1.21875 5.60352 0.952148 5.87695 0.952148 6.21875C0.952148 6.56055 1.22559 6.84082 1.56738 6.84082ZM1.56738 10.4229H14.4258C14.7676 10.4229 15.0479 10.1426 15.0479 9.80078C15.0479 9.45898 14.7744 9.18555 14.4258 9.18555H1.56738C1.21875 9.18555 0.952148 9.45898 0.952148 9.80078C0.952148 10.1426 1.22559 10.4229 1.56738 10.4229ZM1.56738 14.0049H8.75879C9.10059 14.0049 9.38086 13.7246 9.38086 13.3828C9.38086 13.041 9.10742 12.7676 8.75879 12.7676H1.56738C1.21875 12.7676 0.952148 13.041 0.952148 13.3828C0.952148 13.7246 1.22559 14.0049 1.56738 14.0049Z">
                                                        </path>
                                                    </svg></div>
                                                <div
                                                    style="white-space: nowrap; overflow: hidden; text-overflow: ellipsis;">
                                                    Update: 01</div>
                                            </div>
                                        </div>
                                    </div>
                                    <div
                                        style="display: flex; margin-left: 4px; height: 100%; flex: 1 1 auto; flex-direction: column; min-width: 0px;">
                                        <div
                                            style="display: flex; align-items: center; margin-left: 4px; height: 100%; flex: 1 1 auto; min-width: 0px;">
                                            <div class="notion-focusable" role="button" aria-disabled="true"
                                                tabindex="-1"
                                                style="user-select: none; transition: background 20ms ease-in 0s; display: flex; align-items: center; border-radius: 3px; width: 100%; min-height: 34px; padding: 6px 8px 7px; font-size: 14px; overflow: hidden; color: rgba(55, 53, 47, 0.5);">
                                                <div>Empty</div>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                            <div>
                                <div style="display: flex; padding-bottom: 4px; width: 100%;">
                                    <div
                                        style="display: flex; align-items: center; height: 34px; width: 160px; flex: 0 0 auto; color: rgba(55, 53, 47, 0.65);">
                                        <div class="notion-focusable" role="button" aria-disabled="true" tabindex="-1"
                                            style="user-select: none; transition: background 20ms ease-in 0s; display: flex; align-items: center; height: 100%; width: 100%; border-radius: 3px; padding: 0px 6px;">
                                            <div
                                                style="display: flex; align-items: center; line-height: 120%; font-size: 14px; min-width: 0px;">
                                                <div style="margin-right: 8px;"><svg viewBox="0 0 16 16"
                                                        class="typesText"
                                                        style="width: 18px; height: 18px; display: block; fill: rgba(55, 53, 47, 0.45); flex-shrink: 0; backface-visibility: hidden;">
                                                        <path
                                                            d="M1.56738 3.25879H14.4258C14.7676 3.25879 15.0479 2.97852 15.0479 2.63672C15.0479 2.29492 14.7744 2.02148 14.4258 2.02148H1.56738C1.21875 2.02148 0.952148 2.29492 0.952148 2.63672C0.952148 2.97852 1.22559 3.25879 1.56738 3.25879ZM1.56738 6.84082H14.4258C14.7676 6.84082 15.0479 6.56055 15.0479 6.21875C15.0479 5.87695 14.7744 5.60352 14.4258 5.60352H1.56738C1.21875 5.60352 0.952148 5.87695 0.952148 6.21875C0.952148 6.56055 1.22559 6.84082 1.56738 6.84082ZM1.56738 10.4229H14.4258C14.7676 10.4229 15.0479 10.1426 15.0479 9.80078C15.0479 9.45898 14.7744 9.18555 14.4258 9.18555H1.56738C1.21875 9.18555 0.952148 9.45898 0.952148 9.80078C0.952148 10.1426 1.22559 10.4229 1.56738 10.4229ZM1.56738 14.0049H8.75879C9.10059 14.0049 9.38086 13.7246 9.38086 13.3828C9.38086 13.041 9.10742 12.7676 8.75879 12.7676H1.56738C1.21875 12.7676 0.952148 13.041 0.952148 13.3828C0.952148 13.7246 1.22559 14.0049 1.56738 14.0049Z">
                                                        </path>
                                                    </svg></div>
                                                <div
                                                    style="white-space: nowrap; overflow: hidden; text-overflow: ellipsis;">
                                                    Update: 02</div>
                                            </div>
                                        </div>
                                    </div>
                                    <div
                                        style="display: flex; margin-left: 4px; height: 100%; flex: 1 1 auto; flex-direction: column; min-width: 0px;">
                                        <div
                                            style="display: flex; align-items: center; margin-left: 4px; height: 100%; flex: 1 1 auto; min-width: 0px;">
                                            <div class="notion-focusable" role="button" aria-disabled="true"
                                                tabindex="-1"
                                                style="user-select: none; transition: background 20ms ease-in 0s; display: flex; align-items: center; border-radius: 3px; width: 100%; min-height: 34px; padding: 6px 8px 7px; font-size: 14px; overflow: hidden; color: rgba(55, 53, 47, 0.5);">
                                                <div>Empty</div>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                <div style="margin: 0px;"></div>
                <div style="width: 100%; height: 1px; background: rgba(55, 53, 47, 0.09); margin-bottom: 8px;"></div>
                <div class="notion-page-view-discussion" style="width: 100%; margin: 0px auto;">
                    <div data-block-id="29ec6a24-ffba-48a9-833f-9ac8833cfa92"
                        class="notion-selectable notion-page-block">
                        <div style="margin: 14px -14px;">
                            <div style="position: relative;">
                                <div>
                                    <div
                                        style="display: flex; align-items: flex-start; position: relative; font-size: 14px;">
                                        <div style="flex-grow: 1; min-width: 0px;">
                                            <div
                                                style="align-items: center; position: relative; display: flex; flex-direction: row; padding: 6px 16px 0px 18px; user-select: none;">
                                                <div style="margin-right: 10px; margin-top: 2px; user-select: none;">
                                                    <div
                                                        style="background: white; border-radius: 100%; box-shadow: rgba(15, 15, 15, 0.1) 0px 2px 4px;">
                                                        <div
                                                            style="border-radius: 100%; width: 20px; height: 20px; max-width: 100%; max-height: 100%; display: flex; align-items: center; justify-content: center; user-select: none; opacity: 1;">
                                                            <div style="width: 100%; height: 100%;"><img
                                                                    src="/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fpublic.notion-static.com%2F2df40fbf-830a-450a-a79e-a48b73633b19%2F20210428_003435dddd_2.jpg?width=40&amp;userId=&amp;cache=v2"
                                                                    referrerpolicy="same-origin"
                                                                    style="display: block; object-fit: cover; border-radius: 100%; width: 100%; height: 100%;">
                                                            </div>
                                                        </div>
                                                    </div>
                                                </div>
                                                <div style="overflow: hidden;"><span
                                                        style="font-weight: 600; white-space: normal;">Jo-Pippin</span>
                                                    <div
                                                        style="font-size: 12px; line-height: 16px; color: rgba(55, 53, 47, 0.5); margin: 0px 6px; flex-basis: 140px; white-space: normal; flex-grow: 1; display: inline;">
                                                        <div style="display: inline;">Nov 16</div>
                                                    </div>
                                                </div>
                                            </div>
                                            <div style="padding-left: 47px; padding-right: 16px;">
                                                <div style="cursor: text;"></div>
                                            </div>
                                            <div style="margin: 0px 14px 0px 50px;">
                                                <div data-block-id="9f1942d5-f1d2-40dd-9971-4534f13b854e"
                                                    class="notion-selectable notion-image-block"
                                                    style="margin-top: 8px;">
                                                    <div contenteditable="false" data-content-editable-void="true">
                                                        <div style="display: inline-flex; max-height: 240px;">
                                                            <div class="notion-cursor-default"
                                                                style="position: relative; overflow: hidden; flex-grow: 1;">
                                                                <div style="position: relative;">
                                                                    <div>
                                                                        <div style="height: 100%; width: 100%;"><img
                                                                                src="/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Faad8b351-1e5f-40c9-9e92-bfe54fbc5afb%2FUntitled.png?table=block&amp;id=9f1942d5-f1d2-40dd-9971-4534f13b854e&amp;spaceId=e2d7caa2-1739-4bf9-820e-f159a253f176&amp;width=2000&amp;userId=&amp;cache=v2"
                                                                                referrerpolicy="same-origin"
                                                                                style="display: block; object-fit: cover; border-radius: 1px; pointer-events: auto; width: auto; height: auto; max-height: 240px; max-width: 100%; cursor: zoom-in;">
                                                                        </div>
                                                                    </div>
                                                                </div>
                                                            </div>
                                                        </div>
                                                    </div>
                                                </div>
                                            </div>
                                            <div style="margin: 4px 14px 4px 50px;"></div>
                                        </div>
                                    </div>
                                </div>
                                <div>
                                    <div
                                        style="display: flex; align-items: flex-start; position: relative; font-size: 14px;">
                                        <div style="flex-grow: 1; min-width: 0px;">
                                            <div
                                                style="align-items: center; position: relative; display: flex; flex-direction: row; padding: 6px 16px 0px 18px; user-select: none;">
                                                <div style="margin-right: 10px; margin-top: 2px; user-select: none;">
                                                    <div
                                                        style="background: white; border-radius: 100%; box-shadow: rgba(15, 15, 15, 0.1) 0px 2px 4px;">
                                                        <div
                                                            style="border-radius: 100%; width: 20px; height: 20px; max-width: 100%; max-height: 100%; display: flex; align-items: center; justify-content: center; user-select: none; opacity: 1;">
                                                            <div style="width: 100%; height: 100%;"><img
                                                                    src="/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fpublic.notion-static.com%2F2df40fbf-830a-450a-a79e-a48b73633b19%2F20210428_003435dddd_2.jpg?width=40&amp;userId=&amp;cache=v2"
                                                                    referrerpolicy="same-origin"
                                                                    style="display: block; object-fit: cover; border-radius: 100%; width: 100%; height: 100%;">
                                                            </div>
                                                        </div>
                                                    </div>
                                                </div>
                                                <div style="overflow: hidden;"><span
                                                        style="font-weight: 600; white-space: normal;">Jo-Pippin</span>
                                                    <div
                                                        style="font-size: 12px; line-height: 16px; color: rgba(55, 53, 47, 0.5); margin: 0px 6px; flex-basis: 140px; white-space: normal; flex-grow: 1; display: inline;">
                                                        <div style="display: inline;">Nov 18</div>
                                                    </div>
                                                </div>
                                            </div>
                                            <div style="padding-left: 47px; padding-right: 16px;"></div>
                                            <div style="padding: 0px 16px 3px;">
                                                <div style="position: relative;">
                                                    <div style="display: -webkit-box; -webkit-box-orient: vertical;">
                                                        <div>
                                                            <div spellcheck="true" data-content-editable-leaf="true"
                                                                contenteditable="false"
                                                                style="max-width: 100%; width: 100%; white-space: pre-wrap; word-break: break-word; caret-color: rgb(55, 53, 47); cursor: text; padding-left: 32px;">
                                                                Update: 01 | added option to extend monday opening range
                                                                to the end of the week</div>
                                                        </div>
                                                    </div>
                                                </div>
                                            </div>
                                            <div style="margin: 0px 14px 0px 50px;">
                                                <div data-block-id="c54290a8-976d-468e-8818-f394953395e3"
                                                    class="notion-selectable notion-image-block"
                                                    style="margin-top: 8px;">
                                                    <div contenteditable="false" data-content-editable-void="true">
                                                        <div style="display: inline-flex; max-height: 240px;">
                                                            <div class="notion-cursor-default"
                                                                style="position: relative; overflow: hidden; flex-grow: 1;">
                                                                <div style="position: relative;">
                                                                    <div>
                                                                        <div style="height: 100%; width: 100%;"><img
                                                                                src="/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fe8b9e89a-45f1-4c72-b437-3e389547f38f%2FUntitled.png?table=block&amp;id=c54290a8-976d-468e-8818-f394953395e3&amp;spaceId=e2d7caa2-1739-4bf9-820e-f159a253f176&amp;width=2000&amp;userId=&amp;cache=v2"
                                                                                referrerpolicy="same-origin"
                                                                                style="display: block; object-fit: cover; border-radius: 1px; pointer-events: auto; width: auto; height: auto; max-height: 240px; max-width: 100%; cursor: zoom-in;">
                                                                        </div>
                                                                    </div>
                                                                </div>
                                                            </div>
                                                        </div>
                                                    </div>
                                                </div>
                                            </div>
                                            <div style="margin: 4px 14px 4px 50px;"></div>
                                        </div>
                                    </div>
                                </div>
                                <div>
                                    <div
                                        style="display: flex; align-items: flex-start; position: relative; font-size: 14px;">
                                        <div style="flex-grow: 1; min-width: 0px;">
                                            <div
                                                style="align-items: center; position: relative; display: flex; flex-direction: row; padding: 6px 16px 0px 18px; user-select: none;">
                                                <div style="margin-right: 10px; margin-top: 2px; user-select: none;">
                                                    <div
                                                        style="background: white; border-radius: 100%; box-shadow: rgba(15, 15, 15, 0.1) 0px 2px 4px;">
                                                        <div
                                                            style="border-radius: 100%; width: 20px; height: 20px; max-width: 100%; max-height: 100%; display: flex; align-items: center; justify-content: center; user-select: none; opacity: 1;">
                                                            <div style="width: 100%; height: 100%;"><img
                                                                    src="/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fpublic.notion-static.com%2F2df40fbf-830a-450a-a79e-a48b73633b19%2F20210428_003435dddd_2.jpg?width=40&amp;userId=&amp;cache=v2"
                                                                    referrerpolicy="same-origin"
                                                                    style="display: block; object-fit: cover; border-radius: 100%; width: 100%; height: 100%;">
                                                            </div>
                                                        </div>
                                                    </div>
                                                </div>
                                                <div style="overflow: hidden;"><span
                                                        style="font-weight: 600; white-space: normal;">Jo-Pippin</span>
                                                    <div
                                                        style="font-size: 12px; line-height: 16px; color: rgba(55, 53, 47, 0.5); margin: 0px 6px; flex-basis: 140px; white-space: normal; flex-grow: 1; display: inline;">
                                                        <div style="display: inline;">Nov 20</div>
                                                    </div>
                                                </div>
                                            </div>
                                            <div style="padding-left: 47px; padding-right: 16px;"></div>
                                            <div style="padding: 0px 16px 3px;">
                                                <div style="position: relative;">
                                                    <div style="display: -webkit-box; -webkit-box-orient: vertical;">
                                                        <div>
                                                            <div spellcheck="true" data-content-editable-leaf="true"
                                                                contenteditable="false"
                                                                style="max-width: 100%; width: 100%; white-space: pre-wrap; word-break: break-word; caret-color: rgb(55, 53, 47); cursor: text; padding-left: 32px;">
                                                                Update: labels </div>
                                                        </div>
                                                    </div>
                                                </div>
                                            </div>
                                            <div style="margin: 0px 14px 0px 50px;">
                                                <div data-block-id="9fd06621-39b0-4310-9027-a4473adb561d"
                                                    class="notion-selectable notion-image-block"
                                                    style="margin-top: 8px;">
                                                    <div contenteditable="false" data-content-editable-void="true">
                                                        <div style="display: inline-flex; max-height: 240px;">
                                                            <div class="notion-cursor-default"
                                                                style="position: relative; overflow: hidden; flex-grow: 1;">
                                                                <div style="position: relative;">
                                                                    <div>
                                                                        <div style="height: 100%; width: 100%;"><img
                                                                                src="/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fbd91cfe4-bd6d-4e58-a540-ec9aaf137847%2FUntitled.png?table=block&amp;id=9fd06621-39b0-4310-9027-a4473adb561d&amp;spaceId=e2d7caa2-1739-4bf9-820e-f159a253f176&amp;width=2000&amp;userId=&amp;cache=v2"
                                                                                referrerpolicy="same-origin"
                                                                                style="display: block; object-fit: cover; border-radius: 1px; pointer-events: auto; width: auto; height: auto; max-height: 240px; max-width: 100%; cursor: zoom-in;">
                                                                        </div>
                                                                    </div>
                                                                </div>
                                                            </div>
                                                        </div>
                                                    </div>
                                                </div>
                                            </div>
                                            <div style="margin: 4px 14px 4px 50px;"></div>
                                        </div>
                                    </div>
                                </div>
                                <div>
                                    <div
                                        style="display: flex; align-items: flex-start; position: relative; font-size: 14px;">
                                        <div style="flex-grow: 1; min-width: 0px;">
                                            <div
                                                style="align-items: center; position: relative; display: flex; flex-direction: row; padding: 6px 16px 0px 18px; user-select: none;">
                                                <div style="margin-right: 10px; margin-top: 2px; user-select: none;">
                                                    <div
                                                        style="background: white; border-radius: 100%; box-shadow: rgba(15, 15, 15, 0.1) 0px 2px 4px;">
                                                        <div
                                                            style="border-radius: 100%; width: 20px; height: 20px; max-width: 100%; max-height: 100%; display: flex; align-items: center; justify-content: center; user-select: none; opacity: 1;">
                                                            <div style="width: 100%; height: 100%;"><img
                                                                    src="/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fpublic.notion-static.com%2F2df40fbf-830a-450a-a79e-a48b73633b19%2F20210428_003435dddd_2.jpg?width=40&amp;userId=&amp;cache=v2"
                                                                    referrerpolicy="same-origin"
                                                                    style="display: block; object-fit: cover; border-radius: 100%; width: 100%; height: 100%;">
                                                            </div>
                                                        </div>
                                                    </div>
                                                </div>
                                                <div style="overflow: hidden;"><span
                                                        style="font-weight: 600; white-space: normal;">Jo-Pippin</span>
                                                    <div
                                                        style="font-size: 12px; line-height: 16px; color: rgba(55, 53, 47, 0.5); margin: 0px 6px; flex-basis: 140px; white-space: normal; flex-grow: 1; display: inline;">
                                                        <div style="display: inline;">Nov 20</div>
                                                    </div>
                                                </div>
                                            </div>
                                            <div style="padding-left: 47px; padding-right: 16px;"></div>
                                            <div style="margin: 0px 14px 0px 50px;">
                                                <div data-block-id="00239d17-1723-4dc5-b9c8-2d205a838686"
                                                    class="notion-selectable notion-image-block"
                                                    style="margin-top: 8px;">
                                                    <div contenteditable="false" data-content-editable-void="true">
                                                        <div style="display: inline-flex; max-height: 240px;">
                                                            <div class="notion-cursor-default"
                                                                style="position: relative; overflow: hidden; flex-grow: 1;">
                                                                <div style="position: relative;">
                                                                    <div>
                                                                        <div style="height: 100%; width: 100%;"><img
                                                                                src="/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F3e476a6b-c4f1-4394-b4aa-dcf4684b3ce2%2FUntitled.png?table=block&amp;id=00239d17-1723-4dc5-b9c8-2d205a838686&amp;spaceId=e2d7caa2-1739-4bf9-820e-f159a253f176&amp;width=1540&amp;userId=&amp;cache=v2"
                                                                                referrerpolicy="same-origin"
                                                                                style="display: block; object-fit: cover; border-radius: 1px; pointer-events: auto; width: auto; height: auto; max-height: 240px; max-width: 100%; cursor: zoom-in;">
                                                                        </div>
                                                                    </div>
                                                                </div>
                                                            </div>
                                                        </div>
                                                    </div>
                                                </div>
                                            </div>
                                            <div style="margin: 4px 14px 4px 50px;"></div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                <div style="width: 100%; height: 1px; background: rgba(55, 53, 47, 0.09); margin-bottom: 8px;"></div>
                <div class="notion-page-details-controls"
                    style="display: flex; align-items: baseline; justify-content: flex-start; flex-wrap: wrap; color: rgba(55, 53, 47, 0.5); font-family: ui-sans-serif, -apple-system, BlinkMacSystemFont, &quot;Segoe UI&quot;, Helvetica, &quot;Apple Color Emoji&quot;, Arial, sans-serif, &quot;Segoe UI Emoji&quot;, &quot;Segoe UI Symbol&quot;;">
                </div>
            </div>
        </div>
    </div>
</div>