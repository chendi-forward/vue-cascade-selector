<template>
   <selector :init="selectorConstructor" :handle="selectorHandle"></selector>
</template>

<script>
  import Vue from 'vue';
  import Selector from 'vue-cascade-selector';

  var data = {
      "options": {
        "level-1-1": {
            "key": "level-1", 
            "name": "level-1-1", 
            "children": {
              "level-2-1": {
                "key": "level-2",
                "name": "level-2-1",
                "children": {
                  "level-3-1": {
                    "key": "level-3",
                    "name": "level-3-1",
                    "id": "1"
                  },
                  "level-3-2": {
                    "key": "level-3",
                    "name": "level-3-2",
                    "id": "2"
                  },
                  "level-3-3": {
                    "key": "level-3",
                    "name": "level-3-3",
                    "id": "3"
                  }
                }
              },
              "level-2-2": {
                "key": "level-2",
                "name": "level-2-2",
                "children": {
                  "level-3-1": {
                    "key": "level-3",
                    "name": "level-3-1",
                    "id": "1"
                  },
                  "level-3-2": {
                    "key": "level-3",
                    "name": "level-3-2",
                    "id": "2"
                  },
                  "level-3-3": {
                    "key": "level-3",
                    "name": "level-3-3",
                    "id": "3"
                  }
                }
              },
              "level-2-3": {
                "key": "level-2",
                "name": "level-2-3",
                "children": {
                  "level-3-1": {
                    "key": "level-3",
                    "name": "level-3-1",
                    "id": "1"
                  },
                  "level-3-2": {
                    "key": "level-3",
                    "name": "level-3-2",
                    "id": "2"
                  },
                  "level-3-3": {
                    "key": "level-3",
                    "name": "level-3-3",
                    "id": "3"
                  }
                }
              },
            }
        },
        "level-1-2": {
            "key": "level-1", 
            "name": "level-1-2", 
            "children": {
              "level-2-1": {
                "key": "level-2",
                "name": "level-2-1",
                "children": {
                  "level-3-1": {
                    "key": "level-3",
                    "name": "level-3-1",
                    "id": "1"
                  },
                  "level-3-2": {
                    "key": "level-3",
                    "name": "level-3-2",
                    "id": "2"
                  },
                  "level-3-3": {
                    "key": "level-3",
                    "name": "level-3-3",
                    "id": "3"
                  }
                }
              },
              "level-2-2": {
                "key": "level-2",
                "name": "level-2-2",
                "children": {
                  "level-3-1": {
                    "key": "level-3",
                    "name": "level-3-1",
                    "id": "1"
                  },
                  "level-3-2": {
                    "key": "level-3",
                    "name": "level-3-2",
                    "id": "2"
                  },
                  "level-3-3": {
                    "key": "level-3",
                    "name": "level-3-3",
                    "id": "3"
                  }
                }
              },
              "level-2-3": {
                "key": "level-2",
                "name": "level-2-3",
                "children": {
                  "level-3-1": {
                    "key": "level-3",
                    "name": "level-3-1",
                    "id": "1"
                  },
                  "level-3-2": {
                    "key": "level-3",
                    "name": "level-3-2",
                    "id": "2"
                  },
                  "level-3-3": {
                    "key": "level-3",
                    "name": "level-3-3",
                    "id": "3"
                  }
                }
              },
            }
        },
        "level-1-3": {
            "key": "level-1", 
            "name": "level-1-3", 
            "children": {
              "level-2-1": {
                "key": "level-2",
                "name": "level-2-1",
                "children": {
                  "level-3-1": {
                    "key": "level-3",
                    "name": "level-3-1",
                    "id": "1"
                  },
                  "level-3-2": {
                    "key": "level-3",
                    "name": "level-3-2",
                    "id": "2"
                  },
                  "level-3-3": {
                    "key": "level-3",
                    "name": "level-3-3",
                    "id": "3"
                  }
                }
              },
              "level-2-2": {
                "key": "level-2",
                "name": "level-2-2",
                "children": {
                  "level-3-1": {
                    "key": "level-3",
                    "name": "level-3-1",
                    "id": "1"
                  },
                  "level-3-2": {
                    "key": "level-3",
                    "name": "level-3-2",
                    "id": "2"
                  },
                  "level-3-3": {
                    "key": "level-3",
                    "name": "level-3-3",
                    "id": "3"
                  }
                }
              },
              "level-2-3": {
                "key": "level-2",
                "name": "level-2-3",
                "children": {
                  "level-3-1": {
                    "key": "level-3",
                    "name": "level-3-1",
                    "id": "1"
                  },
                  "level-3-2": {
                    "key": "level-3",
                    "name": "level-3-2",
                    "id": "2"
                  },
                  "level-3-3": {
                    "key": "level-3",
                    "name": "level-3-3",
                    "id": "3"
                  }
                }
              },
            }
        },
      },
  }

  export default{
      components: {
        Selector,
      },
      methods: {
        selectorConstructor(that){
  
          that.options = data.options;
          
          that.showSelector = {
            'level-1': {
              'level-1-1': that.options['level-1-1'],
              'level-1-2': that.options['level-1-2'],
              'level-1-3': that.options['level-1-3'],
            }
          };
          
          that.nameMap = {
            'level-1': 'level 1',
            'level-2': 'level 2',
            'level-3': 'level 3'
          };
        },
        selectorHandle(key, value, id){
          console.log(id);
        }
    }
  }
</script>
