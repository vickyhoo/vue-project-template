<template>
  <el-row :gutter="30">
    <el-col :span="6">
      <div>
        <label>Collapsed (current page is under Group of pages 1)</label>
      </div>
      <el-menu theme="dark" active-name="1.1">
        <template v-for="(item, index) in menus">
          <el-submenu :index="index+''" v-if="item.children && item.children.length" :key="item.key" :name="item.key">
            <template slot="title">
              {{item.title}}
            </template>
            <template v-for="(sub,i) in item.children">
              <el-submenu :index="`${index}_${i}`" v-if="sub.children && sub.children.length" :key="sub.key" :name="sub.key">
                <template slot="title">
                  {{sub.title}}
                </template>
                <template v-for="(sub,ii) in sub.children">
                  <el-menu-item :index="`${index}_${i}_${ii}`" :name="sub.key" :key="sub.key">{{sub.title}}</el-menu-item>
                </template>
              </el-submenu>
              <el-menu-item :index="`${index}_${i}`" v-else :name="sub.key" :key="sub.key">{{sub.title}}</el-menu-item>
            </template>
          </el-submenu>
          <el-menu-item :index="index+''" v-else :name="item.key" :key="item.key">{{item.title}}</el-menu-item>
        </template>
      </el-menu>
    </el-col>
    <el-col :span="6">
      <div>
        <label>Expanded (Page 1.1 is current page)</label>
      </div>
      <el-menu theme="dark" :open-names="['1']" active-name="1.1">
        <template v-for="(item,index) in menus">
          <el-submenu :index="index+''" v-if="item.children && item.children.length" :key="item.key" :name="item.key">
            <template slot="title">
              {{item.title}}
            </template>
            <template v-for="(sub,i) in item.children">
              <el-submenu :index="`${index}_${i}`" v-if="sub.children && sub.children.length" :key="sub.key" :name="sub.key">
                <template slot="title">
                  {{sub.title}}
                </template>
                <template v-for="(sub,ii) in sub.children">
                  <el-menu-item :index="`${index}_${i}_${ii}`" :name="sub.key" :key="sub.key">{{sub.title}}</el-menu-item>
                </template>
              </el-submenu>
              <el-menu-item :index="`${index}_${i}`" v-else :name="sub.key" :key="sub.key">{{sub.title}}</el-menu-item>
            </template>
          </el-submenu>
          <el-menu-item :index="index+''" v-else :name="item.key" :key="item.key">{{item.title}}</el-menu-item>
        </template>
      </el-menu>
    </el-col>
    <el-col :span="6">
      <div>
        <label>Hovering on a specific item</label>
      </div>
      <el-menu theme="dark">
        <template v-for="(item ,index) in menus">
          <el-submenu :index="index+''" v-if="item.children && item.children.length" :key="item.key" :name="item.key">
            <template slot="title">
              {{item.title}}
            </template>
            <template v-for="(sub,i) in item.children">
              <el-submenu :index="`${index}_${i}`" v-if="sub.children && sub.children.length" :key="sub.key" :name="sub.key">
                <template slot="title">
                  {{sub.title}}
                </template>
                <template v-for="(sub,ii) in sub.children">
                  <el-menu-item :index="`${index}_${i}_${ii}`" :name="sub.key" :key="sub.key">{{sub.title}}</el-menu-item>
                </template>
              </el-submenu>
              <el-menu-item :index="`${index}_${i}`" v-else :name="sub.key" :key="sub.key">{{sub.title}}</el-menu-item>
            </template>
          </el-submenu>
          <el-menu-item :index="index+''" v-else :name="item.key" :key="item.key">{{item.title}}</el-menu-item>
        </template>
      </el-menu>
    </el-col>
    <el-col :span="6">
      <div>
        <label>Subgroup expanded</label>
      </div>
      <el-menu default-active="1_0" theme="dark" :open-names="['1', '1.3']" active-name="1.1">
        <template v-for="(item, index) in menus" >
          <el-submenu :index="index+''" v-if="item.children && item.children.length" :key="item.key" :name="item.key">
            <template slot="title">
              {{item.title}}
            </template>
            <template v-for="(sub,i) in item.children">
              <el-submenu :index="`${index}_${i}`" v-if="sub.children && sub.children.length" :key="sub.key" :name="sub.key">
                <template slot="title">
                  {{sub.title}}
                </template>
                <template v-for="(sub,ii) in sub.children">
                  <el-menu-item :index="`${index}_${i}_${ii}`" :name="sub.key" :key="sub.key">{{sub.title}}</el-menu-item>
                </template>
              </el-submenu>
              <el-menu-item :index="`${index}_${i}`" v-else :name="sub.key" :key="sub.key">{{sub.title}}</el-menu-item>
            </template>
          </el-submenu>
          <el-menu-item :index="index+''" v-else :name="item.key" :key="item.key">{{item.title}}</el-menu-item>
        </template>
      </el-menu>
    </el-col>
  </el-row>
</template>

<script>
export default {
  data() {
    return {
      menus: [
        { key: '0', title: 'Stand alone page 0' },
        {
          key: '1',
          title: 'Group of pages 1',
          children: [
            { key: '1.1', title: 'Page 1.1' },
            { key: '1.2', title: 'Page 1.2' },
            {
              key: '1.3',
              title: 'Subgroup 1.3',
              children: [
                { key: '1.3.1', title: 'Page 1.3.1' },
                { key: '1.3.2', title: 'Page 1.3.2' }
              ]
            }
          ]
        },
        {
          key: '2',
          title: 'Group of pages 2',
          children: [{ key: '2.1', title: 'Page 2.1' }, { key: '2.2', title: 'Page 2.2' }]
        },
        { key: '3', title: 'Stand alone page 3' }
      ]
    }
  }
}
</script>

<style>
</style>
