<template>
	<AppDoc name="TabMenuDemo" :sources="sources" :extPages="pages" github="tabmenu/TabMenuDemo.vue" >
        <h5>Import</h5>
<pre v-code.script><code>
import TabMenu from 'primevue/tabmenu';

</code></pre>

        <h5>MenuModel</h5>
        <p>TabMenu uses the common MenuModel API to define the items, visit <router-link to="/menumodel">MenuModel API</router-link> for details.</p>

		<h5>Getting Started</h5>
		<p>TabMenu requires a collection of menuitems as its model.</p>
<pre v-code><code>
&lt;TabMenu :model="items" /&gt;

</code></pre>

<pre v-code.script><code>
export default {
	data() {
		return {
			items: [
                {label: 'Home', icon: 'pi pi-fw pi-home'},
                {label: 'Calendar', icon: 'pi pi-fw pi-calendar'},
                {label: 'Edit', icon: 'pi pi-fw pi-pencil'},
                {label: 'Documentation', icon: 'pi pi-fw pi-file'},
                {label: 'Settings', icon: 'pi pi-fw pi-cog'}
            ]
		}
	}
}

</code></pre>

        <p>TabMenu can be also integrated with Vue Router.</p>
        <pre v-code><code>
&lt;TabMenu :model="items" /&gt;
&lt;router-view /&gt;

</code></pre>

<pre v-code.script><code>
export default {
	data() {
		return {
			items: [
                {label: 'Home', icon: 'pi pi-fw pi-home', to: '/tabmenu'},
                {label: 'Calendar', icon: 'pi pi-fw pi-calendar', to: '/tabmenu/calendar'},
                {label: 'Edit', icon: 'pi pi-fw pi-pencil', to: '/tabmenu/edit'},
                {label: 'Documentation', icon: 'pi pi-fw pi-file', to: '/tabmenu/documentation'},
                {label: 'Settings', icon: 'pi pi-fw pi-cog', to: '/tabmenu/settings'}
            ]
		}
	}
}

</code></pre>

        <h5>Active</h5>
        <p>Visibility of the content is specified with the activeIndex property that supports one or two-way binding.</p>

<pre v-code><code>
&lt;TabMenu :model="items" :activeIndex="activeIndex" /&gt;

</code></pre>

        <p>Two-way binding requires v-model.</p>
<pre v-code><code>
&lt;TabMenu :model="items" v-model:activeIndex="activeIndex" /&gt;

</code></pre>

        <h5>Templating</h5>
        <p>TabMenu offers content customization with the <i>item</i> template that receives the menuitem instance from the model as a parameter.</p>
<pre v-code><code><template v-pre>
&lt;TabMenu :model="items"&gt;
    &lt;template #item="{item}"&gt;
        &lt;a :href="item.url"&gt;{{item.label}}&lt;/a&gt;
    &lt;/template&gt;
&lt;/TabMenu&gt;
</template>
</code></pre>

        <h5>Properties</h5>
        <p>Any property as style and class are passed to the main container element. Following are the additional properties to configure the component.</p>
		<div class="doc-tablewrapper">
			<table class="doc-table">
				<thead>
                    <tr>
                        <th>Name</th>
                        <th>Type</th>
                        <th>Default</th>
                        <th>Description</th>
                    </tr>
				</thead>
				<tbody>
                    <tr>
                        <td>model</td>
                        <td>array</td>
                        <td>null</td>
                        <td>An array of menuitems.</td>
                    </tr>
                    <tr>
                        <td>exact</td>
                        <td>boolean</td>
                        <td>true</td>
                        <td>Defines if active route highlight should match the exact route path.</td>
                    </tr>
                    <tr>
                        <td>activeIndex</td>
                        <td>number</td>
                        <td>0</td>
                        <td>Active index of menuitem.</td>
                    </tr>
				</tbody>
			</table>
		</div>

        <h5>Events</h5>
		<div class="doc-tablewrapper">
			<table class="doc-table">
				<thead>
                    <tr>
                        <th>Name</th>
                        <th>Parameters</th>
                        <th>Description</th>
                    </tr>
				</thead>
				<tbody>
                    <tr>
                        <td>tab-change</td>
                        <td>event.originalEvent: Browser event  <br/>
                            event.index: Index of the selected tab
                        </td>
                        <td>Callback to invoke when an active tab is changed.</td>
                    </tr>
				</tbody>
			</table>
		</div>

        <h5>Slots</h5>
		<div class="doc-tablewrapper">
            <table class="doc-table">
				<thead>
               <tr>
                  <th>Name</th>
                  <th>Parameters</th>
               </tr>
				</thead>
				<tbody>
               <tr>
                  <td>item</td>
                  <td>item: Menuitem instance</td>
               </tr>
				</tbody>
			</table>
      </div>

		<h5>Styling</h5>
		<p>Following is the list of structural style classes, for theming classes visit <router-link to="/theming">theming</router-link> page.</p>
		<div class="doc-tablewrapper">
			<table class="doc-table">
				<thead>
                    <tr>
                        <th>Name</th>
                        <th>Element</th>
                    </tr>
				</thead>
				<tbody>
                    <tr>
                        <td>p-tabmenu</td>
                        <td>Container element.</td>
                    </tr>
                    <tr>
                        <td>p-tabmenu-nav</td>
                        <td>List element.</td>
                    </tr>
                    <tr>
                        <td>p-tabmenuitem</td>
                        <td>Menuitem element.</td>
                    </tr>
                    <tr>
                        <td>p-highlight</td>
                        <td>Active menuitem element.</td>
                    </tr>
                    <tr>
                        <td>p-menuitem-icon</td>
                        <td>Icon of a menuitem.</td>
                    </tr>
                    <tr>
                        <td>p-menuitem-text</td>
                        <td>Text of a menuitem.</td>
                    </tr>
				</tbody>
			</table>
		</div>

		<h5>Dependencies</h5>
		<p>None.</p>
    </AppDoc>
</template>

<script>
export default {
    data() {
        return {
            sources: {
                'options-api': {
                    tabName: 'Options API Source',
                    content: `
<template>
    <div>
        <div class="card">
            <h5>Default</h5>
            <TabMenu :model="items" />
            <router-view/>
        </div>
            
        <div class="card">
            <h5>Programmatic</h5>
            <div class="p-py-2">
                <Button @click="active = 0" class="p-button-text" label="Activate 1st" />
                <Button @click="active = 1" class="p-button-text p-mr-2" label="Activate 2nd" />
                <Button @click="active = 2" class="p-button-text p-mr-2" label="Activate 3rd" />
            </div>

            <TabMenu :model="items2" v-model:activeIndex="active" />
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            active: 3,
            items: [
                {
                    label: 'Home',
                    icon: 'pi pi-fw pi-home',
                    to: '/'
                },
                {
                    label: 'Calendar',
                    icon: 'pi pi-fw pi-calendar',
                    to: '/calendar'
                },
                {
                    label: 'Edit',
                    icon: 'pi pi-fw pi-pencil',
                    to: '/edit'
                },
                {
                    label: 'Documentation',
                    icon: 'pi pi-fw pi-file',
                    to: '/documentation'
                },
                {
                    label: 'Settings',
                    icon: 'pi pi-fw pi-cog',
                    to: '/settings'
                }
            ],
            items2: [
                {
                    label: 'Home',
                    icon: 'pi pi-fw pi-home'
                },
                {
                    label: 'Calendar',
                    icon: 'pi pi-fw pi-calendar'
                },
                {
                    label: 'Edit',
                    icon: 'pi pi-fw pi-pencil'
                },
                {
                    label: 'Documentation',
                    icon: 'pi pi-fw pi-file'
                },
                {
                    label: 'Settings',
                    icon: 'pi pi-fw pi-cog'
                }
            ]
        }
    }
}
<\\/script>

<style scoped lang="scss">
::v-deep(.tabmenudemo-content) {
    padding: 2rem 1rem;
}
</style>`
                },
                'composition-api': {
                    tabName: 'Composition API Source',
                    content: `
<template>
    <div>
        <div class="card">
            <h5>Default</h5>
            <TabMenu :model="items" />
            <router-view/>
        </div>
            
        <div class="card">
            <h5>Programmatic</h5>
            <div class="p-py-2">
                <Button @click="active = 0" class="p-button-text" label="Activate 1st" />
                <Button @click="active = 1" class="p-button-text p-mr-2" label="Activate 2nd" />
                <Button @click="active = 2" class="p-button-text p-mr-2" label="Activate 3rd" />
            </div>

            <TabMenu :model="items2" v-model:activeIndex="active" />
        </div>
    </div>
</template>

<script>
import { ref } from 'vue';

export default {
    setup() {
        const active = ref(3);
        const items = ref([
            {
                label: 'Home',
                icon: 'pi pi-fw pi-home',
                to: '/'
            },
            {
                label: 'Calendar',
                icon: 'pi pi-fw pi-calendar',
                to: '/calendar'
            },
            {
                label: 'Edit',
                icon: 'pi pi-fw pi-pencil',
                to: '/edit'
            },
            {
                label: 'Documentation',
                icon: 'pi pi-fw pi-file',
                to: '/documentation'
            },
            {
                label: 'Settings',
                icon: 'pi pi-fw pi-cog',
                to: '/settings'
            }
        ]);
        const items2 = ref([
            {
                label: 'Home',
                icon: 'pi pi-fw pi-home'
            },
            {
                label: 'Calendar',
                icon: 'pi pi-fw pi-calendar'
            },
            {
                label: 'Edit',
                icon: 'pi pi-fw pi-pencil'
            },
            {
                label: 'Documentation',
                icon: 'pi pi-fw pi-file'
            },
            {
                label: 'Settings',
                icon: 'pi pi-fw pi-cog'
            }
        ]);
        
        return { active, items, items2 }
    }
}
<\\/script>

<style scoped lang="scss">
::v-deep(.tabmenudemo-content) {
    padding: 2rem 1rem;
}
</style>`
                }
            },
            pages: [
                    {
                        tabName: 'HomeDemo',
                        content: `
<template>
    <div class="tabmenudemo-content">
        <h5>Home Component Content</h5>
    </div>
</template>

<script>
export default {

}
<\\/script>
`
                    },
                    {
                        tabName: 'CalendarDemo',
                        content: `
<template>
    <div class="tabmenudemo-content">
        <h5>Calendar Component Content</h5>
    </div>
</template>

<script>
export default {

}
<\\/script>
`
                    },
                    {
                        tabName: 'EditDemo',
                        content: `
<template>
    <div class="tabmenudemo-content">
        <h5>Edit Component Content</h5>
    </div>
</template>

<script>
export default {

}
<\\/script>
`
                    },
                    {
                        tabName: 'DocumentationDemo',
                        content: `
<template>
    <div class="tabmenudemo-content">
        <h5>Documentation Component Content</h5>
    </div>
</template>

<script>
export default {

}
<\\/script>
`
                    },
                    {
                        tabName: 'SettingsDemo',
                        content: `
<template>
    <div class="tabmenudemo-content">
        <h5>Settings Component Content</h5>
    </div>
</template>

<script>
export default {

}
<\\/script>`
                    }
                ]
        }
    }
}
</script>
