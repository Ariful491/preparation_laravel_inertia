<script setup>
import {Head, Link} from '@inertiajs/vue3';
import {useEditor, EditorContent} from '@tiptap/vue-3'
import StarterKit from '@tiptap/starter-kit'

import Table from '@tiptap/extension-table'
import TableCell from '@tiptap/extension-table-cell'
import TableHeader from '@tiptap/extension-table-header'
import TableRow from '@tiptap/extension-table-row'

import Underline from '@tiptap/extension-underline'
import MenuIcon from 'vue-material-design-icons/Menu.vue';
import FormatBold from 'vue-material-design-icons/FormatBold.vue'



const editor = useEditor({
    content: '<p>I’m running Tiptap with Vue.js. 🎉</p>',
    extensions: [
        StarterKit,
        Underline, Table, TableCell, TableHeader, TableRow

    ],
    editorProps: {
        attributes: {
            class: 'border-spacing-1 border-2   border-gray-400 shadow-md  prose  p-3 mx-6 min-h-[12rem] max-h-[12rem] overflow-y-auto outline-none max-w-none',
        }
    }
})
</script>

<template>
    <Head title="Editor Tester TIPTOP"/>
    <div class="border-spacing-1 border-2 rounded-xl border-gray-400 shadow-md  p-3 m-6 active:bg-gray-500">
        <input type="text"
               class="border-spacing-1 border-2 rounded-xl border-gray-400 shadow-md  p-3 m-6 active:bg-gray-500"/>

    </div>
    <div class="container mx-auto max-w-full  ">
        <div class="grid grid-cols-2  ">
            <div>
                <section class="buttons mx-6 flex items-center flex-wrap gap-x-4 border border-gray-400 p-4">
                    <div v-if="editor" class="justify-items-center">
                        <button class="py-1 px-4 bg-blue-400 hover:bg-blue-900   m-1 rounded"
                                @click="editor.chain().focus().toggleBold().run()"
                                :disabled="!editor.can().chain().focus().toggleBold().run()"
                                :class="{ 'bg-blue-100': editor.isActive('bold') }">
                             <FormatBold/>
                        </button>
                        <button class="py-1 px-4 bg-blue-400 hover:bg-blue-900   m-1 rounded"
                                @click="editor.chain().focus().toggleItalic().run()"
                                :disabled="!editor.can().chain().focus().toggleItalic().run()"
                                :class="{ 'bg-blue-100': editor.isActive('italic') }">
                            italic
                        </button>

                        <button class="py-1 px-4 bg-blue-400 hover:bg-blue-900   m-1 rounded"
                                @click="editor.chain().focus().toggleCode().run()"
                                :disabled="!editor.can().chain().focus().toggleCode().run()"
                                :class="{ 'bg-blue-100': editor.isActive('code') }">
                            code
                        </button>


                        <button class="py-1 px-4 bg-blue-400 hover:bg-blue-900   m-1 rounded"
                                @click="editor.chain().focus().toggleHeading({ level: 1 }).run()"
                                :class="{ 'bg-blue-100': editor.isActive('heading', { level: 1 }) }">
                            h1
                        </button>
                        <button class="py-1 px-4 bg-blue-400 hover:bg-blue-900   m-1 rounded"
                                @click="editor.chain().focus().toggleHeading({ level: 2 }).run()"
                                :class="{ 'bg-blue-100': editor.isActive('heading', { level: 2 }) }">
                            h2
                        </button>
                        <button class="py-1 px-4 bg-blue-400 hover:bg-blue-900   m-1 rounded"
                                @click="editor.chain().focus().toggleHeading({ level: 3 }).run()"
                                :class="{ 'bg-blue-100': editor.isActive('heading', { level: 3 }) }">
                            h3
                        </button>
                        <button class="py-1 px-4 bg-blue-400 hover:bg-blue-900   m-1 rounded"
                                @click="editor.chain().focus().toggleHeading({ level: 4 }).run()"
                                :class="{ 'bg-blue-100': editor.isActive('heading', { level: 4 }) }">
                            h4
                        </button>
                        <button class="py-1 px-4 bg-blue-400 hover:bg-blue-900   m-1 rounded"
                                @click="editor.chain().focus().toggleHeading({ level: 5 }).run()"
                                :class="{ 'bg-blue-100': editor.isActive('heading', { level: 5 }) }">
                            h5
                        </button>
                        <button class="py-1 px-4 bg-blue-400 hover:bg-blue-900   m-1 rounded"
                                @click="editor.chain().focus().toggleHeading({ level: 6 }).run()"
                                :class="{ 'bg-blue-100': editor.isActive('heading', { level: 6 }) }">
                            h6
                        </button>
                        <button class="py-1 px-4 bg-blue-400 hover:bg-blue-900   m-1 rounded"
                                @click="editor.chain().focus().toggleBulletList().run()"
                                :class="{ 'bg-blue-100': editor.isActive('bulletList') }">
                            bullet list
                        </button>
                        <button class="py-1 px-4 bg-blue-400 hover:bg-blue-900   m-1 rounded"
                                @click="editor.chain().focus().toggleOrderedList().run()"
                                :class="{ 'bg-blue-100': editor.isActive('orderedList') }">
                            ordered list
                        </button>

                        <button class="py-1 px-4 bg-blue-400 hover:bg-blue-900   m-1 rounded"
                                @click="editor.chain().focus().toggleBlockquote().run()"
                                :class="{ 'bg-blue-100': editor.isActive('blockquote') }">
                            blockquote
                        </button>
                        <button class="py-1 px-4 bg-blue-400 hover:bg-blue-900   m-1 rounded"
                                @click="editor.chain().focus().setHorizontalRule().run()"
                        >
                            Hr
                        </button>
                        <button class="py-1 px-4 bg-blue-400 hover:bg-blue-900   m-1 rounded"
                                @click="editor.chain().focus().setHardBreak().run()">
                            hard break
                        </button>
                        <button class="py-1 px-4 bg-blue-400 hover:bg-blue-900   m-1 rounded"
                                @click="editor.chain().focus().undo().run()"
                                :disabled="!editor.can().chain().focus().undo().run()">
                            undo
                        </button>
                        <button class="py-1 px-4 bg-blue-400 hover:bg-blue-900   m-1 rounded"
                                @click="editor.chain().focus().redo().run()"
                                :disabled="!editor.can().chain().focus().redo().run()">
                            redo
                        </button>

                        <button class="py-1 px-4 bg-blue-400 hover:bg-blue-900   m-1 rounded"
                                @click="editor.chain().focus().toggleUnderline().run()"
                                :class="{ 'is-active': editor.isActive('underline') }">
                            toggleUnderline
                        </button>


                        <button
                            @click="editor.chain().focus().insertTable({ rows: 3, cols: 3, withHeaderRow: true }).run()">
                            insertTable
                        </button>


                        <button @click="editor.chain().focus().addColumnBefore().run()">
                            addColumnBefore
                        </button>
                        <button @click="editor.chain().focus().addColumnAfter().run()">
                            addColumnAfter
                        </button>
                        <button @click="editor.chain().focus().deleteColumn().run()">
                            deleteColumn
                        </button>
                        <button @click="editor.chain().focus().addRowBefore().run()">
                            addRowBefore
                        </button>
                        <button @click="editor.chain().focus().addRowAfter().run()">
                            addRowAfter
                        </button>
                        <button @click="editor.chain().focus().deleteRow().run()">
                            deleteRow
                        </button>
                        <button @click="editor.chain().focus().deleteTable().run()">
                            deleteTable
                        </button>
                        <button @click="editor.chain().focus().mergeCells().run()">
                            mergeCells
                        </button>
                        <button @click="editor.chain().focus().splitCell().run()">
                            splitCell
                        </button>
                        <button @click="editor.chain().focus().toggleHeaderColumn().run()">
                            toggleHeaderColumn
                        </button>
                        <button @click="editor.chain().focus().toggleHeaderRow().run()">
                            toggleHeaderRow
                        </button>
                        <button @click="editor.chain().focus().toggleHeaderCell().run()">
                            toggleHeaderCell
                        </button>
                        <button @click="editor.chain().focus().mergeOrSplit().run()">
                            mergeOrSplit
                        </button>
                        <button @click="editor.chain().focus().setCellAttribute('colspan', 2).run()">
                            setCellAttribute
                        </button>
                        <button @click="editor.chain().focus().fixTables().run()">
                            fixTables
                        </button>
                        <button @click="editor.chain().focus().goToNextCell().run()">
                            goToNextCell
                        </button>
                        <button @click="editor.chain().focus().goToPreviousCell().run()">
                            goToPreviousCell
                        </button>

                    </div>
                </section>
                <EditorContent :editor="editor"/>
            </div>
        </div>


    </div>

</template>

<style >
button {
    padding: 10px;
    margin: 10px;
    background: red;
}


</style>
