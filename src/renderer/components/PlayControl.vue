<script setup>
import { storeToRefs } from 'pinia';
import { usePlayStore } from '../store/playStore';
import { useAppCommonStore } from '../store/appCommonStore';

const props = defineProps({
    toggleQueueAction: Function,
})


const { playing, playMode } = storeToRefs(usePlayStore())
const { playPrevTrack, togglePlay, playNextTrack, switchPlayMode } = usePlayStore()
const { togglePlaybackQueueView, hideAllCategoryViews, 
    hideAllCtxMenus, hidePlayingThemeListView } = useAppCommonStore()

const togglePlaybackQueue = () => {
    hideAllCategoryViews()
    hideAllCtxMenus()
    hidePlayingThemeListView()
    
    const { toggleQueueAction } = props
    if(typeof toggleQueueAction == 'function') {
        toggleQueueAction()
    } else {
        togglePlaybackQueueView()
    }
}
</script>

<template>
    <div class="play-ctl">
        <div class="play-mode-btn" @click="switchPlayMode">
            <svg v-show="playMode == 0" width="21" height="21" viewBox="5 0 20 30" xmlns="http://www.w3.org/2000/svg">
                <title />
                <g data-name="Layer 2" id="Layer_2">
                    <g id="Interface-Solid">
                        <g id="interface-solid-multimedia-refresh-button-2">
                            <path
                                d="M28.75,17.77671a1.24991,1.24991,0,0,0-1.25,1.25,2.73109,2.73109,0,0,1-2.67578,2.77734H9.122l3.48254-3.57227a1.25,1.25,0,0,0-1.78906-1.74609L5.2627,22.181a1.25046,1.25046,0,0,0,0,1.7461l5.55273,5.69531a1.25,1.25,0,1,0,1.78906-1.7461L9.122,24.30405H24.8418c.00653,0,.0119-.00366.01837-.00366A5.23207,5.23207,0,0,0,30,19.02671,1.24991,1.24991,0,0,0,28.75,17.77671Z" />
                            <path
                                d="M20.87805,8.19467l-3.48254,3.57227A1.25,1.25,0,1,0,19.18457,13.513L24.7373,7.81772a1.25045,1.25045,0,0,0,0-1.74609L19.18457.37631a1.25,1.25,0,1,0-1.78906,1.7461l3.48254,3.57226H5.1582c-.00653,0-.0119.00367-.01837.00367A5.23207,5.23207,0,0,0,0,10.972a1.25,1.25,0,0,0,2.5,0A2.7311,2.7311,0,0,1,5.17578,8.19467Z" />
                        </g>
                    </g>
                </g>
            </svg>
            <svg v-show="playMode == 1" width="21" height="21" viewBox="0 0 30 29.99936" xmlns="http://www.w3.org/2000/svg">
                <title />
                <g data-name="Layer 2" id="Layer_2">
                    <g id="Interface-Solid">
                        <g id="interface-solid-multimedia-refresh-button-3">
                            <path
                                d="M29.98035,2.15171a1.19758,1.19758,0,0,0-.04944-.24463,1.20863,1.20863,0,0,0-.08985-.23438c-.01574-.02978-.017-.06323-.0354-.09228a1.171,1.171,0,0,0-.09118-.09546,1.23677,1.23677,0,0,0-.583-.40845,1.19606,1.19606,0,0,0-.25208-.051A1.15361,1.15361,0,0,0,28.75.99936c-.03455,0-.06354.01685-.09735.01953a1.51168,1.51168,0,0,0-.47968.13965c-.02978.01563-.063.01685-.09192.03516l-1.5.95019A1.23783,1.23783,0,0,0,27.5,4.41489v7.33447a1.25,1.25,0,0,0,2.5,0v-9.5C30,2.21469,29.98309,2.18564,29.98035,2.15171Z" />
                            <path
                                d="M28.75,17.77671a1.24991,1.24991,0,0,0-1.25,1.25,2.73109,2.73109,0,0,1-2.67578,2.77734H9.122l3.48254-3.57227a1.25,1.25,0,0,0-1.78906-1.74609L5.2627,22.181a1.25046,1.25046,0,0,0,0,1.7461l5.55273,5.69531a1.25,1.25,0,1,0,1.78906-1.7461L9.122,24.30405H24.8418c.00653,0,.0119-.00366.01837-.00366A5.23207,5.23207,0,0,0,30,19.02671,1.24991,1.24991,0,0,0,28.75,17.77671Z" />
                            <path
                                d="M20.87805,8.19467l-3.48254,3.57227A1.25,1.25,0,1,0,19.18457,13.513L24.7373,7.81772a1.25045,1.25045,0,0,0,0-1.74609L19.18457.37631a1.25,1.25,0,1,0-1.78906,1.7461l3.48254,3.57226H5.1582c-.00653,0-.0119.00367-.01837.00367A5.23207,5.23207,0,0,0,0,10.972a1.25,1.25,0,0,0,2.5,0A2.7311,2.7311,0,0,1,5.17578,8.19467Z" />
                        </g>
                    </g>
                </g>
            </svg>
            <svg v-show="playMode == 2" width="21" height="21" viewBox="0 0 895.9 896.32"
                xmlns="http://www.w3.org/2000/svg">
                <g id="Layer_2" data-name="Layer 2">
                    <g id="Layer_1-2" data-name="Layer 1">
                        <path
                            d="M448.44,580.41c-8.56,13.17-16.15,26.54-25.33,38.7q-75.37,99.78-199.73,115A294.9,294.9,0,0,1,189,736c-52,.19-104,.12-156,.06C14.94,736.05.84,723,0,705.86c-.88-18.65,13.41-33.67,32.4-33.73,31.16-.11,62.33,0,93.49,0,21.33,0,42.67.09,64,0,65.54-.3,121.23-23.93,166.11-71.71,32.9-35,52.2-76.81,58.09-124.6,11.25-91.24-33-178.37-113.58-223.59-32-17.93-66.44-27.53-103.06-27.88-54.82-.52-109.66-.15-164.49-.23C15,224.05.85,211,0,193.88c-.89-18.66,13.39-33.69,32.38-33.75q48.74-.16,97.49,0c27.49.11,55.07-.78,82.45,1.05,68.7,4.61,128,31.51,178.11,78.69a280.59,280.59,0,0,1,55.11,72.49c.62,1.16,1.31,2.28,2.32,4,1.07-1.72,1.94-3,2.69-4.37Q518.32,190.7,654.77,164.59c16.58-3.16,33.75-3.84,50.69-4.32,24.82-.69,49.66-.18,74.5-.18h6.65c-1.86-2-3-3.21-4.2-4.41q-49.9-49.79-99.83-99.56C672.21,45.8,669,33.68,674.29,20,682.17-.2,707.91-6.44,724.61,7.5c1.65,1.38,3.17,2.94,4.7,4.47L884.16,166.82c15.68,15.69,15.64,34.91-.09,50.64q-78,78-155.92,155.91c-11.49,11.48-26.29,14.11-39.22,7.09-19.47-10.57-23-35.65-7-51.7q39.87-40,80-79.82c8-8,15.91-16,24.5-24.62-2.09-.1-3.34-.22-4.58-.22-26,0-52-.15-78,0C600,224.8,510.64,294.93,486.46,394.56a224,224,0,0,0,130.21,259.8A215.56,215.56,0,0,0,699.17,672c27.83.35,55.66.12,83.49.14.94,0,1.88-.08,3.67-.16-1.73-1.87-2.86-3.19-4.09-4.42q-50.09-50-100.16-99.94c-15.9-15.94-12.75-40.76,6.3-51.51a32,32,0,0,1,36.41,3.6c1.77,1.5,3.4,3.19,5.05,4.84L884,678.64c15.93,15.93,15.9,35-.09,51Q805.95,807.6,728,885.54c-11.4,11.38-26.35,13.91-39.26,6.8-19-10.49-22.74-35.36-7.29-51,19.07-19.35,38.45-38.38,57.66-57.6,15.54-15.55,31-31.17,47.38-47.62h-5.83c-24.83,0-49.68.5-74.49-.08q-170.7-4-255.77-152.23Z" />
                    </g>
                </g>
            </svg>
        </div>
        <div class="play-prev-btn spacing" @click="playPrevTrack">
            <!--
            <svg width="18" height="18" viewBox="0 0 24 28.01" xmlns="http://www.w3.org/2000/svg"><g id="Layer_2" data-name="Layer 2"><g id="Layer_1-2" data-name="Layer 1"><g id="Layer_2-2" data-name="Layer 2"><path d="M1.2,28a1.12,1.12,0,0,0,1.2-1V16L22.09,27.81a1.37,1.37,0,0,0,1.68-.21A.92.92,0,0,0,24,27V1a1.11,1.11,0,0,0-1.2-1,1.45,1.45,0,0,0-.71.19L2.4,12V1A1.12,1.12,0,0,0,1.2,0,1.12,1.12,0,0,0,0,1V27A1.12,1.12,0,0,0,1.2,28Z"/></g></g></g></svg>
            -->
            <svg width="17" height="17" viewBox="0 0 892.88 974.69" xmlns="http://www.w3.org/2000/svg">
                <g id="Layer_2" data-name="Layer 2">
                    <g id="Layer_1-2" data-name="Layer 1">
                        <path
                            d="M892.87,488q0,214.21-.11,428.45c0,10.43-.53,21.09-2.67,31.25-4.61,21.79-18.28,30.2-40,26a74.83,74.83,0,0,1-28.75-12.19q-179-124.53-358.08-249.08Q331.34,620.65,199.38,529.05c-16.55-11.48-24-27.38-23.76-46.84.25-19.07,8-34.58,24.16-45.7Q506.41,225.91,813,15.23A128.65,128.65,0,0,1,833,4c26.35-11.87,53.86,3.42,58.72,32.54A99.92,99.92,0,0,1,892.82,53Q892.91,270.47,892.87,488Z" />
                        <path
                            d="M98.92,487.37q0,217.73,0,435.46c0,23.51-12.2,41.44-32.87,48.51-30,10.25-60.8-7.94-65.78-39-.65-4,.12-8.27.12-12.4Q.38,487.7.29,55.49c0-14,2.41-26.8,11.87-37.61A49.79,49.79,0,0,1,67.24,4c19.28,7.09,31.62,24.93,31.64,46.42q.12,133.48,0,267Z" />
                    </g>
                </g>
            </svg>
        </div>
        <div class="play-btn spacing" 
            :class="{
                playing,
                paused: !playing,
                loading: false,
            }"
            @click="togglePlay">
            <svg v-show="!playing" width="18" height="18" viewBox="0 0 139 139" xml:space="preserve"
                xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
                <path
                    d="M117.037,61.441L36.333,14.846c-2.467-1.424-5.502-1.424-7.972,0c-2.463,1.423-3.982,4.056-3.982,6.903v93.188  c0,2.848,1.522,5.479,3.982,6.9c1.236,0.713,2.61,1.067,3.986,1.067c1.374,0,2.751-0.354,3.983-1.067l80.704-46.594  c2.466-1.422,3.984-4.054,3.984-6.9C121.023,65.497,119.502,62.866,117.037,61.441z" />
            </svg>
            <!--
            <svg v-show="playing" width="24" height="24" class="paused" viewBox="0 0 100 100" xml:space="preserve" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"><path d="M44.2,78.3H32.1c-1.1,0-2-0.9-2-2V23.7c0-1.1,0.9-2,2-2h12.1c1.1,0,2,0.9,2,2v52.5C46.2,77.4,45.3,78.3,44.2,78.3z"/><path d="M67.9,78.3H55.8c-1.1,0-2-0.9-2-2V23.7c0-1.1,0.9-2,2-2h12.1c1.1,0,2,0.9,2,2v52.5C69.9,77.4,69,78.3,67.9,78.3z"/></svg>
            -->
            <svg v-show="playing" width="16" height="16"  viewBox="0 0 658.53 1006.16"
                xmlns="http://www.w3.org/2000/svg">
                <g id="Layer_2" data-name="Layer 2">
                    <g id="Layer_1-2" data-name="Layer 1">
                        <path
                            d="M196.43,503.09q0,200.21,0,400.41c0,20.63-4.42,39.93-15.66,57.45-21.43,33.42-62.66,50.43-102.18,42.14-39.72-8.34-70.5-39.72-76.82-78.67A130.29,130.29,0,0,1,.08,903.55Q-.06,501.88,0,100.21C0,48.38,35,8.27,86.47.9,136.62-6.29,186.73,30.61,194.7,80.79a135,135,0,0,1,1.66,20.88Q196.49,302.37,196.43,503.09Z" />
                        <path
                            d="M462.09,503q0-200.72,0-401.42c0-46.91,29.11-85.51,72.86-97,63.42-16.69,123.47,30.29,123.52,96.79q.12,169,0,337.92,0,232.95,0,465.9c0,38.9-15.56,69.86-50.23,88.7-60,32.57-134.91-2.14-145.21-73a117,117,0,0,1-.9-17Q462.05,703.43,462.09,503Z" />
                    </g>
                </g>
            </svg>
            <svg v-show="false" width="17" height="17" viewBox="0 0 847.92 853.23" xmlns="http://www.w3.org/2000/svg">
                <g id="Layer_2" data-name="Layer 2">
                    <g id="Layer_1-2" data-name="Layer 1">
                        <g id="Layer_2-2" data-name="Layer 2">
                            <g id="Layer_1-2-2" data-name="Layer 1-2">
                                <path d="M722.91,136.61c0-17.65-.35-35.3.09-52.93.58-23,19.65-41,42.64-40.9A42.56,42.56,0,0,1,808,85.56v0c.16,38.17,0,76.33,0,114.49v54.5c-.07,25.68-18.46,44.14-44.12,44.16q-84.75.08-169.49,0c-21.66-.07-38.86-15.64-42.08-37.35-2.94-19.81,9.9-39.91,29.79-45.85a54.59,54.59,0,0,1,15.26-1.9c25.16-.19,50.32-.09,76.53-.09a51.87,51.87,0,0,0-3-4.35c-53.4-65-120.89-107-204.41-119.23-120.29-17.69-221,21.23-301.17,112-43.89,49.66-69.09,108.57-79,174-.8,5.26-1.24,10.59-2.17,15.83-3.89,21.83-24.31,37.22-46,34.82C15.69,424.12-1.76,405.28.14,383A356.16,356.16,0,0,1,9.31,326.4C42,196.44,117.61,100.17,237.93,40.47,302.23,8.56,371-4,442.53,1.11,551,9,642.25,53.63,717.11,132.23l4.7,5Z"/>
                                <path d="M125.34,715.25v6.31c0,16.16.27,32.34-.19,48.49-.65,23-19.8,40.89-42.82,40.71-22.63-.18-42-18.42-42.1-41q-.48-87,0-174c.12-22.34,19.12-40.8,41.66-40.89,57.32-.22,114.65-.09,172,0a40.33,40.33,0,0,1,7.43.81A42.52,42.52,0,0,1,296,600.34c-1.35,21.43-18.92,39-40.45,39.47-24.82.49-49.66.18-74.48.21h-6.55a21.06,21.06,0,0,0,1.55,2.93c53.45,65.66,121.36,107.14,205.23,120.83,132.88,21.7,259.15-40.37,328.92-148.61a342.29,342.29,0,0,0,53-149.18c2.45-21.73,19.28-38.14,40-39.15,21.49-1.06,40.64,12.81,44,34.06,1.62,10.24.12,21.26-1.49,31.69-11.52,74.95-40.28,142.66-87.62,202-66,82.72-150.85,135.93-255.6,152.64-144.38,23-267.87-20.37-370.17-124.57C130.27,720.55,128.32,718.41,125.34,715.25Z"/>
                            </g>
                        </g>
                    </g>
                </g>
            </svg>
        </div>
        <div class="play-next-btn spacing" @click="playNextTrack">
            <!--
            <svg width="18" height="18" viewBox="0 0 24 28.01" xmlns="http://www.w3.org/2000/svg"><g id="Layer_2" data-name="Layer 2"><g id="Layer_1-2" data-name="Layer 1"><g id="Layer_2-2" data-name="Layer 2"><path d="M22.8,0a1.12,1.12,0,0,0-1.2,1V12L1.91.19A1.37,1.37,0,0,0,.23.41.89.89,0,0,0,0,1V27a1.12,1.12,0,0,0,1.2,1,1.36,1.36,0,0,0,.71-.2L21.6,16V27A1.22,1.22,0,0,0,24,27V1A1.12,1.12,0,0,0,22.8,0Z"/></g></g></g></svg>
            -->
            <svg width="17" height="17" viewBox="0 0 892.89 974.72" xmlns="http://www.w3.org/2000/svg">
                <g id="Layer_2" data-name="Layer 2">
                    <g id="Layer_1-2" data-name="Layer 1">
                        <path
                            d="M0,487.1q0-214.48.11-429c0-10.43.55-21.09,2.72-31.24C7.49,5.16,21.25-3.21,43,1.09A75.6,75.6,0,0,1,71.71,13.35Q238,129.06,404.36,244.75,551,346.75,697.57,448.84c14.66,10.26,20.1,26.31,19.71,43.82-.43,19.08-8.14,34.53-24.32,45.64Q386.35,748.89,79.78,959.58a131.15,131.15,0,0,1-19.56,11c-26.27,12-54-3.06-59-32.1A96.76,96.76,0,0,1,.06,922.05Q0,704.58,0,487.1Z" />
                        <path
                            d="M794,486.76q0-217.47,0-434.95c0-23.46,12.26-41.43,32.93-48.47,30-10.21,60.81,8,65.73,39.13.64,4-.13,8.26-.13,12.4q0,432.21.09,864.41c0,14-2.45,26.8-11.92,37.6a49.8,49.8,0,0,1-55.1,13.81c-19.25-7.11-31.56-25-31.57-46.47q-.12-133.49,0-267Z" />
                    </g>
                </g>
            </svg>
        </div>
        <div class="playlist-btn spacing" @click.stop="togglePlaybackQueue">
            <svg width="17" height="17" viewBox="0 0 682.28 597.06" xmlns="http://www.w3.org/2000/svg">
                <g id="Layer_2" data-name="Layer 2">
                    <g id="Layer_1-2" data-name="Layer 1">
                        <path
                            d="M597.41,348.87v-7.12q0-148.73,0-297.45c0-21.61,12.87-38.33,33-43.16,25.6-6.14,51,13.32,51.67,39.64.14,5.33.07,10.66.07,16,0,136.81.29,273.62-.14,410.42-.17,54.89-25.81,95.18-75.43,118.3-76.43,35.63-167.21-14.9-178.41-98.26C418.79,417.15,465.4,354,535,342.85a119,119,0,0,1,56.75,4.31C593.32,347.67,594.9,348.11,597.41,348.87Z" />
                        <path
                            d="M255.64,84.82q-104.73,0-209.46.06c-13.1,0-24.79-3.21-33.93-12.94C.19,59.1-3.13,44,3,27.57S21.6,2,39.19.34c2.65-.25,5.32-.29,8-.29Q255.89,0,464.6,0c9.48,0,18.54,1.16,26.81,6.3,15.55,9.68,23.33,28.26,19,45.77-4.53,18.37-19.25,31-37.85,32.44-3.15.24-6.32.29-9.48.29Q359.36,84.84,255.64,84.82Z" />
                        <path
                            d="M234.76,255.4q-95.46,0-190.92,0c-21.35,0-38.21-13.2-42.57-32.94A42.4,42.4,0,0,1,41,170.69c1.33-.06,2.66-.07,4-.07q189.66,0,379.33,0c21.48,0,38,12.15,43.2,31.67,7.08,26.38-12.46,52.85-39.81,53-64.3.27-128.61.09-192.91.09Z" />
                        <path
                            d="M170.39,341.48c42.81,0,85.62-.11,128.42,0,21.15.08,38,14.74,41.44,35.38a42.3,42.3,0,0,1-40.09,49.26c-1.33.07-2.67.07-4,.07q-125.67,0-251.35,0C24.12,426.22,8,414.9,2.16,396.47c-8.51-26.86,11.14-54.69,39.31-54.89,43-.3,85.94-.08,128.92-.08Z" />
                        <path
                            d="M170.48,596.82c-41.64,0-83.28-.08-124.92,0-17.84,0-31.81-6.75-40.39-22.64-14.51-26.86,3.62-59.55,34.07-61.89,2.32-.18,4.66-.28,7-.28q124.41,0,248.84-.06c18.44,0,32.79,6.84,41.31,23.55,13.68,26.81-4.47,58.93-34.5,60.88-12.44.81-25,.37-37.46.39Q217.46,596.87,170.48,596.82Z" />
                    </g>
                </g>
            </svg>
        </div>
    </div>
</template>

<style scoped>
.play-ctl {
    display: flex;
    height: var(--others-playmeta-height);
    align-items: center;
}

.play-ctl div {
    width: fit-content;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

.play-ctl .spacing {
    margin-left: var(--others-playctl-spacing);
}

.play-ctl svg {
    fill: var(--button-icon-btn-color);
    cursor: pointer;
    -webkit-app-region: no-drag;
}

.play-ctl svg:hover {
    fill: var(--content-highlight-color);
}

.play-ctl .play-btn {
    border-radius: 10rem;
    width: 41px;
    height: 41px;
    background: var(--button-icon-text-btn-bg-color);
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
}

.play-ctl .play-btn:hover {
    background: var(--button-icon-text-btn-hover-bg-color);
}

.play-ctl .play-btn svg {
    fill: var(--button-icon-text-btn-icon-color) !important;
}

.play-ctl .play-btn.paused svg {
    transform: translateX(1px) translateY(0.5px);
    /*fill: var(--button-icon-text-btn-icon-color) !important;*/
}

.play-ctl .play-btn.loading svg {
    animation: rotate360 1s infinite;
}
</style>
