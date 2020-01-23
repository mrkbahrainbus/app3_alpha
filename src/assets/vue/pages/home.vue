<template>
  <f7-page @page:beforeremove="onPageBeforeRemove" @page:init="onPageInit" >
  <div class="bg"></div>
  <div class="bg bg2"></div>
  <div class="bg bg3"></div>
    <f7-navbar>
      <f7-nav-left>
        <f7-link class="panel-open" open-panel="left" icon="fas fa-bars"></f7-link>
      </f7-nav-left>
      <div class="title">Red Bus BH</div>
      <f7-nav-right>
        <f7-link
          class="searchbar-enable"
          data-searchbar=".searchbar-components"
          icon="fas fa-search"
        ></f7-link>
      </f7-nav-right>
      <f7-searchbar
        class="searchbar-components"
        search-container=".components-list"
        search-in="a"
        expandable
      ></f7-searchbar>
    </f7-navbar>

<f7-block-title></f7-block-title>
    <f7-block inner>
    </f7-block>

   <f7-card> 
    <f7-tabs animated>
      <f7-tab id="tab-1" class="page-content" tab-active>
        <f7-block>
            <div class="list">
              <ul>
                <li>
                  <a href="#" id="autocomplete-standalone-ajaxOrg" class="item-link item-content autocomplete-opener">
                    <input type="text" placeholder="Select Origin"/>
                      <div class="item-title"></div>
                  </a>
                </li>
                <li>
                  <a href="#" id="autocomplete-standalone-ajaxDest" class="item-link item-content autocomplete-opener">
                    <input type="text" placeholder="Select Destination"/>
                      <div class="item-title"></div>
                  </a>
                </li>
              </ul>
           </div>
           <div>
           <br>
              <f7-button raised fill color="green">Plan Trip</f7-button>
            </div>
        </f7-block>


    </f7-tab>
      <f7-tab id="tab-2" class="page-content">
        <f7-block>
                    <div style="height:180px;overflow-y:scroll;">
                      <f7-card-content :padding="true">
                        <f7-list>
                          <f7-list-item>A1</f7-list-item>
                          <f7-list-item>A2</f7-list-item>
                          <f7-list-item>X3</f7-list-item>
                          <f7-list-item>X2A</f7-list-item>
                          <f7-list-item>X2</f7-list-item>
                          <f7-list-item>X4</f7-list-item>
                          <f7-list-item>X6</f7-list-item>
                          <f7-list-item>10/11</f7-list-item>
                          <f7-list-item>12</f7-list-item>
                          <f7-list-item>13</f7-list-item>
                          <f7-list-item>14/15/16</f7-list-item>
                          <f7-list-item>17/18</f7-list-item>
                          <f7-list-item>19</f7-list-item>
                          <f7-list-item>32/33</f7-list-item>
                          <f7-list-item>41</f7-list-item>
                          <f7-list-item>43</f7-list-item>
                          <f7-list-item>44/45</f7-list-item>
                          <f7-list-item>50</f7-list-item>
                          <f7-list-item>56</f7-list-item>
                          <f7-list-item>70</f7-list-item>
                        </f7-list>
                      </f7-card-content>
                    </div>
                  </f7-block>
      </f7-tab>
      <f7-tab id="tab-3" class="page-content">
        <f7-block>
          <p>Stop List</p>
        </f7-block>
      </f7-tab>
    </f7-tabs>
 </f7-card> 

    <f7-toolbar bottom tabbar>
      <f7-link tab-link="#tab-1" tab-link-active>
        <f7-icon ios="material:directions_bus" md="material:directions_bus">
        </f7-icon>
        <span class="tabbar-label">PLAN</span>
      </f7-link>
      <f7-link tab-link="#tab-2">
        <f7-icon ios="material:directions" md="material:directions">
        </f7-icon>
        <span class="tabbar-label">ROUTES</span>
      </f7-link>
      <f7-link tab-link="#tab-3">
        <f7-icon ios="material:transfer_within_a_station" md="material:transfer_within_a_station"> 
          <!-- <f7-badge color="red">1</f7-badge> -->
         </f7-icon>
        <span class="tabbar-label">STOPS</span>
      </f7-link>
    </f7-toolbar>
  
   
  </f7-page>
</template>

<script>

import { f7Navbar, f7Page, f7BlockTitle } from 'framework7-vue';

 export default {
   components: {
      f7Page,
      f7Navbar,
      f7BlockTitle,
    },
    data() {
      return {
      };
    },
        methods: {
      onPageBeforeRemove() {
        const self = this;
        self.autocompleteStandaloneAjaxO.destroy();
        self.autocompleteStandaloneAjaxD.destroy();
      },
      onPageInit() {
        const self = this;
        const app = self.$f7;
        const $ = self.$$;

        // Standalone With Ajax
        self.autocompleteStandaloneAjax = app.autocomplete.create({
          openIn: 'popup', 
          openerEl: '#autocomplete-standalone-ajaxOrg', 
          closeOnSelect: true, 
          valueProperty: 'name',
          textProperty: 'name', 
          limit: 50,
          preloader: true, 
          source(query, render) {
            const autocomplete = this;
            const results = [];
            if(query.length >= 2){
            autocomplete.preloaderShow();
           
            app.request({
              url: 'https://api.bahrainbus.xyz/api/v1/service/location?10chx=uMPP8ybZHMKq6ZKnWx8Mz4Ks6wfMVVDNUGp&lang=en&q=' + query,
              method: 'GET',
              dataType: 'json',
              data: {
                query,
              },
              success(data) {

                for (let i = 0; i < data.result.length; i += 1) {
                  if (data.result[i].text.toLowerCase().indexOf(query.toLowerCase()) >= 0) results.push(data.result[i].text);
                  autocomplete.preloaderHide();
                  render(results);
                }
              },
            });
          }
          },
          on: {
            
            change(value) {
              $('#autocomplete-standalone-ajaxOrg').find('.item-after').text(value[0]);
              $('#autocomplete-standalone-ajaxOrg').find('input').val(value[0]);
            },
          },
        });

        self.autocompleteStandaloneAjaxD = app.autocomplete.create({
          openIn: 'popup', 
          openerEl: '#autocomplete-standalone-ajaxDest', 
          closeOnSelect: true, 
          valueProperty: 'name',
          textProperty: 'name',
          limit: 50,
          preloader: true,
          source(query, render) {
            const autocomplete = this;
            const results = [];
            // var location ='';
          if (query.length >= 2){
            autocomplete.preloaderShow();
            app.request({
              url: 'https://api.bahrainbus.xyz/api/v1/service/location?10chx=uMPP8ybZHMKq6ZKnWx8Mz4Ks6wfMVVDNUGp&lang=en&q='+query,
              method: 'GET',
              dataType: 'json',
              data: {
                query,
              },
              success(data) {
                // console.log("dta",data)

                for (let i = 0; i < data.result.length; i += 1) {
                  if (data.result[i].text.toLowerCase().indexOf(query.toLowerCase()) >= 0) results.push(data.result[i].text);
                  autocomplete.preloaderHide();
                  render(results);
                }
              },
            });
          }
          },
          on: {
            change(value) {
              $('#autocomplete-standalone-ajaxDest').find('.item-after').text(value[0]);
              $('#autocomplete-standalone-ajaxDest').find('input').val(value[0]);
            },
          },
        });
      },
    },
  };

</script>

<style>
  .bg {
    animation: slide 3s ease-in-out infinite alternate;
    background-image: linear-gradient(-60deg, #6c3 50%, #09f 50%);
    background-image: linear-gradient(-60deg, #fff 50%, #d32f2f 50%);
    bottom: 0;
    left: -50%;
    opacity: .5;
    position: fixed;
    right: -50%;
    top: 0;
    z-index: -1;
  }

  .bg2 {
    animation-direction: alternate-reverse;
    animation-duration: 4s;
  }

  .bg3 {
    animation-duration: 5s;
  }

  @keyframes slide {
    0% {
      transform: translateX(-25%);
    }

    100% {
      transform: translateX(25%);
    }
  }

  .card {
    background: var(--f7-card-bg-color);
    position: absolute;
    border-radius: 8px;
    font-size: var(--f7-card-font-size);
    margin-top: var(--f7-card-margin-vertical);
    margin-bottom: var(--f7-card-margin-vertical);
    margin-left: 0;
    margin-right: calc(var(--f7-card-margin-horizontal) + var(--f7-safe-area-right));
    box-shadow: var(--f7-card-box-shadow);
    width: 100%;
    bottom: 26px;
  }
</style>


