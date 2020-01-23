<template>
  <f7-page @page:beforeremove="onPageBeforeRemove" @page:init="onPageInit">
    <!-- <f7-navbar title="Autocomplete" back-link="Back">
      <div class="subnavbar">
        <form class="searchbar" id="searchbar-autocomplete">
          <div class="searchbar-inner">
            <div class="searchbar-input-wrap">
              <input type="search" placeholder="Search"/>
              <i class="searchbar-icon"></i>
              <span class="input-clear-button"></span>
            </div>
            <span class="searchbar-disable-button" v-if="!$theme.aurora">Cancel</span>
          </div>
        </form>
      </div>
    </f7-navbar> -->

    <!-- <f7-block-title>Dropdown Autocomplete</f7-block-title>
    <div class="block">
      <p>Dropdown autocomplete is good to use as a quick and simple solution to provide more options in addition to free-type value.</p>
    </div>
    <div class="list no-hairlines-md">
      <div class="block-header">Simple Dropdown Autocomplete</div>
      <ul>
        <li class="item-content item-input inline-label">
          <div class="item-inner">
            <div class="item-title item-label">Fruit</div>
            <div class="item-input-wrap">
              <input type="text" placeholder="Fruit" id="autocomplete-dropdown"/>
            </div>
          </div>
        </li>
      </ul>
    </div>
    <div class="list no-hairlines-md">
      <div class="block-header">Dropdown With Input Expand</div>
      <ul>
        <li class="item-content item-input inline-label">
          <div class="item-inner">
            <div class="item-title item-label">Fruit</div>
            <div class="item-input-wrap">
              <input type="text" placeholder="Fruit" id="autocomplete-dropdown-expand"/>
            </div>
          </div>
        </li>
      </ul>
    </div>
    <div class="list no-hairlines-md">
      <div class="block-header">Dropdown With All Values</div>
      <ul>
        <li class="item-content item-input">
          <div class="item-inner">
            <div class="item-title item-label">Fruit</div>
            <div class="item-input-wrap">
              <input type="text" placeholder="Fruit" id="autocomplete-dropdown-all"/>
            </div>
          </div>
        </li>
      </ul>
    </div>
    <div class="list no-hairlines-md">
      <div class="block-header">Dropdown With Placeholder</div>
      <ul>
        <li class="item-content item-input">
          <div class="item-inner">
            <div class="item-title item-label">Fruit</div>
            <div class="item-input-wrap">
              <input type="text" placeholder="Fruit" id="autocomplete-dropdown-placeholder"/>
            </div>
          </div>
        </li>
      </ul>
    </div>
    <div class="list no-hairlines-md">
      <div class="block-header">Dropdown With Typeahead</div>
      <ul>
        <li class="item-content item-input">
          <div class="item-inner">
            <div class="item-title item-label">Fruit</div>
            <div class="item-input-wrap">
              <input type="text" placeholder="Fruit" id="autocomplete-dropdown-typeahead"/>
            </div>
          </div>
        </li>
      </ul>
    </div>
    <div class="list no-hairlines-md">
      <div class="block-header">Dropdown With Ajax-Data</div>
      <ul>
        <li class="item-content item-input">
          <div class="item-inner">
            <div class="item-title item-label">Language</div>
            <div class="item-input-wrap">
              <input type="text" placeholder="Language" id="autocomplete-dropdown-ajax"/>
            </div>
          </div>
        </li>
      </ul>
    </div>
    <div class="list no-hairlines-md">
      <div class="block-header">Dropdown With Ajax-Data + Typeahead</div>
      <ul>
        <li class="item-content item-input">
          <div class="item-inner">
            <div class="item-title item-label">Language</div>
            <div class="item-input-wrap">
              <input type="text" placeholder="Language" id="autocomplete-dropdown-ajax-typeahead"/>
            </div>
          </div>
        </li>
      </ul>
    </div>
    <f7-block-title>Standalone Autocomplete</f7-block-title>
    <div class="block">
      <p>Standalone autocomplete provides better mobile UX by opening it in a new page or popup. Good to use when you need to get strict values without allowing free-type values.</p>
    </div>
    <div class="list">
      <div class="block-header">Simple Standalone Autocomplete</div>
      <ul>
        <li>
          <a href="#" id="autocomplete-standalone" class="item-link item-content autocomplete-opener">
            <input type="hidden"/>
            <div class="item-inner">
              <div class="item-title">Favorite Fruite</div>
              <div class="item-after"></div>
            </div>
          </a>
        </li>
      </ul>
    </div> -->
    <!-- <div class="list">
      <div class="block-header">Popup Autocomplete</div>
      <ul>
        <li>
          <a href="#" id="autocomplete-standalone-popup" class="item-link item-content autocomplete-opener">
            <input type="hidden"/>
            <div class="item-inner">
              <div class="item-title">Favorite Fruite</div>
              <div class="item-after"></div>
            </div>
          </a>
        </li>
      </ul>
    </div>
    <div class="list">
      <div class="block-header">Multiple Values</div>
      <ul>
        <li>
          <a href="#" id="autocomplete-standalone-multiple" class="item-link item-content autocomplete-opener">
            <input type="hidden"/>
            <div class="item-inner">
              <div class="item-title">Favorite Fruite</div>
              <div class="item-after"></div>
            </div>
          </a>
        </li>
      </ul>
    </div> -->
    <div class="list">
      <div class="block-header">With Ajax-Data</div>
      <ul>
        <li>
          <a href="#" id="autocomplete-standalone-ajaxOrg" class="item-link item-content autocomplete-opener">
            <input type="text" placeholder="Select Origin"/>
            <div class="item-inner">
              <div class="item-title"></div>
              <!-- <div class="item-after"></div> -->
            </div>
          </a>
        </li>
        <li>
          <a href="#" id="autocomplete-standalone-ajaxDest" class="item-link item-content autocomplete-opener">
            <input type="text" placeholder="Select Destination"/>
            <div class="item-inner">
              <div class="item-title"></div>
              <!-- <div class="item-after"></div> -->
            </div>
          </a>
        </li>
      </ul>
    </div>
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
        // fruits: 'Apple Apricot Avocado Banana Melon Orange Peach Pear Pineapple'.split(' '),
      };
    },
    methods: {
      onPageBeforeRemove() {
        const self = this;
        // Destroy all autocompletes
        // self.autocompleteDropdownSimple.destroy();
        // self.autocompleteDropdownExpand.destroy();
        // self.autocompleteDropdownAll.destroy();
        // self.autocompleteDropdownPlaceholder.destroy();
        // self.autocompleteDropdownTypeahead.destroy();
        // self.autocompleteDropdownAjax.destroy();
        // self.autocompleteDropdownAjaxTypeahead.destroy();
        // self.autocompleteStandaloneSimple.destroy();
        // self.autocompleteStandalonePopup.destroy();
        // self.autocompleteStandaloneMultiple.destroy();
        self.autocompleteStandaloneAjax.destroy();
      },
      onPageInit() {
        const self = this;
        const app = self.$f7;
        // const fruits = self.fruits;
        const $ = self.$$;


        // Dropdown with ajax data
        // self.autocompleteDropdownAjaxTypeahead = app.autocomplete.create({
        //   inputEl: '#autocomplete-dropdown-ajax-typeahead',
        //   openIn: 'dropdown',
        //   preloader: true, // enable preloader
        //   /* If we set valueProperty to "id" then input value on select will be set according to this property */
        //   valueProperty: 'name', // object's "value" property name
        //   textProperty: 'name', // object's "text" property name
        //   limit: 20, // limit to 20 results
        //   typeahead: true,
        //   dropdownPlaceholderText: 'Origin',
        //   source(query, render) {
        //     const autocomplete = this;
        //     const results = [];
        //     if (query.length === 0) {
        //       render(results);
        //       return;
        //     }
        //     // Show Preloader
        //     autocomplete.preloaderShow();

        //     // Do Ajax request to Autocomplete data
        //     app.request({
        //       url: 'https://api.bahrainbus.xyz/api/v1/service/location?10chx=uMPP8ybZHMKq6ZKnWx8Mz4Ks6wfMVVDNUGp&lang=en&q=manama',
        //       method: 'GET',
        //       dataType: 'json',
        //       // send "query" to server. Useful in case you generate response dynamically
        //       data: {
        //         query,
        //       },
        //       success(data) {
        //       // Find matched items
        //       console.log("Hi data vannu",data.result.length)
        //         for (let i = 0; i < data.result.length; i += 1) {
        //       // console.log("Hi data result vannu",data.result[0].text)
        //           if (data.result[i].text.toLowerCase().indexOf(query.toLowerCase()) === 0) {results.push(data.result[i].text);}
        //         }
        //         // Hide Preoloader
        //         autocomplete.preloaderHide();
        //         // Render items by passing array with result items
        //         render(results);
        //       },
        //     });
        //   },
        // });

        // Standalone With Ajax
        self.autocompleteStandaloneAjax = app.autocomplete.create({
          openIn: 'popup', // open in page
          openerEl: '#autocomplete-standalone-ajaxOrg', // link that opens autocomplete
          closeOnSelect: true, // allow multiple values
          valueProperty: 'name', // object's "value" property name
          textProperty: 'name', // object's "text" property name
          limit: 50,
          preloader: true, // enable preloader
          source(query, render) {
            const autocomplete = this;
            const results = [];
            if (query.length === 0) {
              render(results);
              return;
            }
            // Show Preloader
            autocomplete.preloaderShow();
            // Do Ajax request to Autocomplete data
            app.request({
              url: 'https://api.bahrainbus.xyz/api/v1/service/location?10chx=uMPP8ybZHMKq6ZKnWx8Mz4Ks6wfMVVDNUGp&lang=en&q=manama',
              method: 'GET',
              dataType: 'json',
              // send "query" to server. Useful in case you generate response dynamically
              data: {
                query,
              },
              success(data) {
                // if(data.result.length === 0){
                  
                // }

                for (let i = 0; i < data.result.length; i += 1) {
                  if (data.result[i].text.toLowerCase().indexOf(query.toLowerCase()) >= 0) results.push(data.result[i].text);
                   // Hide Preoloader
                  autocomplete.preloaderHide();
                  // Render items by passing array with result items
                  render(results);
                }
              },
            });
          },
          on: {
            
            change(value) {
              // // Add item value to input value
              $('#autocomplete-standalone-ajaxOrg').find('.item-after').text(value[0]);
              // Add item value to input value
              $('#autocomplete-standalone-ajaxOrg').find('input').val(value[0]);
            },
          },
        });

               // Standalone With Ajax
        self.autocompleteStandaloneAjax = app.autocomplete.create({
          openIn: 'popup', // open in page
          openerEl: '#autocomplete-standalone-ajaxDest', // link that opens autocomplete
          closeOnSelect: true, // allow multiple values
          valueProperty: 'name', // object's "value" property name
          textProperty: 'name', // object's "text" property name
          limit: 50,
          preloader: true, // enable preloader
          source(query, render) {
            const autocomplete = this;
            const results = [];
            if (query.length === 0) {
              render(results);
              return;
            }
            // Show Preloader
            autocomplete.preloaderShow();
            // Do Ajax request to Autocomplete data
            app.request({
              url: 'https://api.bahrainbus.xyz/api/v1/service/location?10chx=uMPP8ybZHMKq6ZKnWx8Mz4Ks6wfMVVDNUGp&lang=en&q=manama',
              method: 'GET',
              dataType: 'json',
              // send "query" to server. Useful in case you generate response dynamically
              data: {
                query,
              },
              success(data) {

                for (let i = 0; i < data.result.length; i += 1) {
                  if (data.result[i].text.toLowerCase().indexOf(query.toLowerCase()) >= 0) results.push(data.result[i].text);
                   // Hide Preoloader
                  autocomplete.preloaderHide();
                  // Render items by passing array with result items
                  render(results);
                }
              },
            });
          },
          on: {
            
            change(value) {
              // // Add item value to input value
              $('#autocomplete-standalone-ajaxDest').find('.item-after').text(value[0]);
              // Add item value to input value
              $('#autocomplete-standalone-ajaxDest').find('input').val(value[0]);
            },
          },
        });
      },
    },
  };
</script>

