<script>
  export default {
    name: 'TabComponent',
    data() {
      return {
        tabs: [
          {
            id: 'list-home',
            title: 'What we do',
            contentTitle: 'Learning Possibilities',
            content: 'Lorem ipsum gravida nibh vel velit auctor aliquetn sollicitudirem quibibendum auci elit cons equat ipsutis sem nibh id elit. Duis sed odio sit amet nibh vulputate cursus a sit amet mauris. Morbi accumsan ipsum velit. Nam nec tellus a odio tincidunt',
            listItems: [
              'We enrich lives through learning.',
              'We enrich lives through learning.',
              'We enrich lives through learning.',
              'We enrich lives through learning.'
            ],
            imgSrc: new URL('../assets/img/h12-tabs-icon-1.png', import.meta.url).href
          },
          {
            id: 'list-profile',
            title: 'Degree programme',
            contentTitle: 'Inspiring Minds',
            content: 'Lorem ipsum gravida nibh vel velit auctor aliquetn sollicitudirem quibibendum auci elit cons equat ipsutis sem nibh id elit. Duis sed odio sit amet nibh vulputate cursus a sit amet mauris. Morbi accumsan ipsum velit. Nam nec tellus a odio tincidunt',
            listItems: [
              'Maximizing potential through individual attention.',
              'We enrich lives through learning.',
              'Enriquecemos vidas a través del aprendizaje.',
              'Nous enrichissons des vies par l\'apprentissage.'
            ],
            imgSrc: new URL('../assets/img/h12-tabs-icon-2.png', import.meta.url).href

          },
          {
            id: 'list-messages',
            title: 'Career achievements',
            contentTitle: 'Investing in Knowledge',
            content: 'Lorem ipsum gravida nibh vel velit auctor aliquetn sollicitudirem quibibendum auci elit cons equat ipsutis sem nibh id elit. Duis sed odio sit amet nibh vulputate cursus a sit amet mauris. Morbi accumsan ipsum velit. Nam nec tellus a odio tincidunt',
            listItems: [
              'We enrich lives through learning.',
              'We enrich lives through learning.',
              'We enrich lives through learning.',
              'We enrich lives through learning.'
            ],
            imgSrc: new URL('../assets/img/h12-tabs-icon-3.png', import.meta.url).href

          },
          {
            id: 'list-settings',
            title: 'Personal management',
            contentTitle: 'Secure Your Future',
            content: 'Lorem ipsum gravida nibh vel velit auctor aliquetn sollicitudirem quibibendum auci elit cons equat ipsutis sem nibh id elit. Duis sed odio sit amet nibh vulputate cursus a sit amet mauris. Morbi accumsan ipsum velit. Nam nec tellus a odio tincidunt',
            listItems: [
              'We enrich lives through learning.',
              'We enrich lives through learning.',
              'We enrich lives through learning.',
              'We enrich lives through learning.'
            ],
            imgSrc: new URL('../assets/img/h12-tabs-icon-4.png', import.meta.url).href

          },
          {
            id: 'list-5',
            title: 'Step to success',
            contentTitle: 'Where Learning Begins',
            content: 'Lorem ipsum gravida nibh vel velit auctor aliquetn sollicitudirem quibibendum auci elit cons equat ipsutis sem nibh id elit. Duis sed odio sit amet nibh vulputate cursus a sit amet mauris. Morbi accumsan ipsum velit. Nam nec tellus a odio tincidunt',
            listItems: [
              'We enrich lives through learning.',
              'We enrich lives attraverso l\'apprendimento.',
              'Enriquecemos vidas a través del aprendizaje.',
              'Nous enrichissons des vies par l\'apprentissage.'
            ],
            imgSrc: new URL('../assets/img/h12-tabs-icon-5.png', import.meta.url).href
          },
          {
            id: 'list-6',
            title: 'Knowledge transfer',
            contentTitle: 'Knowledge is Power',
            content: 'Lorem ipsum gravida nibh vel velit auctor aliquetn sollicitudirem quibibendum auci elit cons equat ipsutis sem nibh id elit. Duis sed odio sit amet nibh vulputate cursus a sit amet mauris. Morbi accumsan ipsum velit. Nam nec tellus a odio tincidunt',
            listItems: [
              'We enrich lives through learning.',
              'We enrich lives attraverso l\'apprendimento.',
              'Enriquecemos vidas a través del aprendizaje.',
              'Nous enrichissons des vies par l\'apprentissage.'
            ],
            imgSrc: new URL('../assets/img/h12-tabs-icon-6.png', import.meta.url).href
          }
        ]
      };
    }
  };
  </script>

<template>
    <div class="row">
      <div class="col-2">
        <div class="list-group" id="list-tab" role="tablist">
          <a
            v-for="(tab, index) in tabs"
            :key="index"
            :class="['list-group-item', 'list-group-item-action', { active: index === 0 }]"
            :id="tab.id + '-tab'"
            data-bs-toggle="list"
            :href="'#' + tab.id"
            role="tab"
            :aria-controls="tab.id"
          >
            {{ tab.title }}
          </a>
        </div>
      </div>
      <div class="col-8">
        <div class="tab-content" id="nav-tabContent">
          <div
            v-for="(tab, index) in tabs"
            :key="index"
            :class="['tab-pane', 'fade', { 'show active': index === 0 }]"
            :id="tab.id"
            role="tabpanel"
            :aria-labelledby="tab.id + '-tab'"
          >
            <div>
                
              <h2>{{ tab.contentTitle }}</h2>
              <p>{{ tab.content }}</p>
              <div class="row">
                <div class="col-5">
                  <ul>
                    <li v-for="(item, itemIndex) in tab.listItems" :key="itemIndex">{{ item }}</li>
                  </ul>
                </div>
                <div class="col-3">
                  <img :src="tab.imgSrc" alt="" />
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  
  
  <style>
  </style>
  
  