<script setup lang="ts">
import { isColorSchemaConfigured, isDark, toggleDark } from '@slidev/client/logic/dark.ts'
import { currentPage, downloadPDF, hasNext, hasPrev, isEmbedded, isPresenter, next, prev, showPresenter, total } from '@slidev/client/logic/nav.ts'
import { showEditor, showInfoDialog, showPresenterCursor, toggleOverview } from '@slidev/client/state/index.ts'
import { brush, drawingEnabled } from '@slidev/client/logic/drawings.ts'
import { configs } from '@slidev/client/env.ts'
import Settings from '@slidev/client/internals/Settings.vue'
import MenuButton from '@slidev/client/internals/MenuButton.vue'
import VerticalDivider from '@slidev/client/internals/VerticalDivider.vue'
</script>

<template>
      <button v-if="!isEmbedded" class="slidev-icon-btn" title="Toggle fullscreen" @click="toggleFullscreen" name="Toggle fullscreen">
        <carbon:minimize v-if="isFullscreen" />
        <carbon:maximize v-else />
      </button>

      <button class="slidev-icon-btn" :class="{ disabled: !hasPrev }" title="Previous slide" @click="prev" name="Previous slide">
        <carbon:arrow-left />
      </button>

      <button class="slidev-icon-btn" :class="{ disabled: !hasNext }" title="Next slide" @click="next" name="Next slide">
        <carbon:arrow-right />
      </button>

      <button v-if="!isEmbedded" class="slidev-icon-btn" title="Slides overview" @click="toggleOverview()" name="Slides overview">
        <carbon:apps />
      </button>

      <button
          v-if="!isColorSchemaConfigured"
          class="slidev-icon-btn"
          title="Toggle dark mode"
          @click="toggleDark()"
          name="Toggle dark mode"
      >
        <carbon-moon v-if="isDark" />
        <carbon-sun v-else />
      </button>

      <VerticalDivider />

      <template v-if="!isEmbedded">
        <template v-if="!isPresenter && !md && RecordingControls">
          <RecordingControls />
          <VerticalDivider />
        </template>

        <button
            v-if="isPresenter"
            class="slidev-icon-btn"
            title="Show presenter cursor"
            @click="showPresenterCursor = !showPresenterCursor"
            name="Show presenter cursor"
        >
          <ph-cursor-fill v-if="showPresenterCursor" />
          <ph-cursor-duotone v-else class="opacity-50" />
        </button>
      </template>
</template>
