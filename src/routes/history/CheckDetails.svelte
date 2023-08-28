<script>
  import Paper, { Title, Content } from '@smui/paper';
  import Accordion, { Panel, Header } from '@smui-extra/accordion';
  import Textfield from '@smui/textfield';
  import Chart from 'chart.js/auto'

  import Tooltip, {
  Wrapper,
  Link,
  RichActions,
} from '@smui/tooltip';
import Button, { Label } from '@smui/button';
import IconButton from '@smui/icon-button';
import Badge from '@smui-extra/badge';
import { Icon } from '@smui/common';
import List, { Item } from '@smui/list';
import { afterUpdate, onMount } from 'svelte';

  Chart.defaults.color = '#FFFFFF';

  export let check;

  let errorCanvas;
  let errorChart;

  let contrastCanvas;
  let contrastChart;

  let alertCanvas;
  let alertChart;

  let featureCanvas;
  let featureChart;

  let structureCanvas;
  let structureChart;

  let ariaCanvas;
  let ariaChart;

  let date = new Date(check.time)


  onMount(init)

  afterUpdate(() => {
    errorChart.destroy();
    contrastChart.destroy();
    alertChart.destroy();
    featureChart.destroy();
    structureChart.destroy();
    ariaChart.destroy();
    init()}
  )

  function init() {
    initError();
    initContrast();
    initAlert();
    initFeature();
    initStructure();
    initAria();
  }

  function initError() {
    errorChart = new Chart(
      errorCanvas.getContext('2d'),
      {
        type: 'bar',
        options: {
          plugins: {
            legend: {
              display: false
            },
          },
          scales: {
            y: {
              min: 0,
              ticks: {
                stepSize: 1
              }
            }
          }
        },
        data: {
          labels: Object.values(check.content.categories.error.items).map(row => row.description),
          datasets: [
            {
              label: 'Count',
              data: Object.values(check.content.categories.error.items).map(row => row.count),
              backgroundColor: '#B22222',
            }
          ]
        }
      }
    );
  }

  function initContrast() {
    contrastChart = new Chart(
      contrastCanvas.getContext('2d'),
      {
        type: 'bar',
        options: {
          plugins: {
            legend: {
              display: false
            },
          },
          scales: {
            y: {
              min: 0,
              ticks: {
                stepSize: 1
              }
            }
          }
        },
        data: {
          labels: Object.values(check.content.categories.contrast.items).map(row => row.description),
          datasets: [
            {
              label: 'Count',
              data: Object.values(check.content.categories.contrast.items).map(row => row.count),
              backgroundColor: '#6495ED',
            }
          ]
        }
      }
    );
  }

  function initAlert() {
    alertChart = new Chart(
      alertCanvas.getContext('2d'),
      {
        type: 'bar',
        options: {
          plugins: {
            legend: {
              display: false
            },
          },
          scales: {
            y: {
              min: 0,
              ticks: {
                stepSize: 1
              }
            }
          }
        },
        data: {
          labels: Object.values(check.content.categories.alert.items).map(row => row.description),
          datasets: [
            {
              label: 'Count',
              data: Object.values(check.content.categories.alert.items).map(row => row.count),
              backgroundColor: '#FFE4B5',
            }
          ]
        }
      }
    );
  }

  function initFeature() {
    featureChart = new Chart(
      featureCanvas.getContext('2d'),
      {
        type: 'bar',
        options: {
          plugins: {
            legend: {
              display: false
            },
          },
          scales: {
            y: {
              min: 0,
              ticks: {
                stepSize: 1
              }
            }
          }
        },
        data: {
          labels: Object.values(check.content.categories.feature.items).map(row => row.description),
          datasets: [
            {
              label: 'Count',
              data: Object.values(check.content.categories.feature.items).map(row => row.count),
              backgroundColor: '#008000',
            }
          ]
        }
      }
    );
  }

  function initStructure() {
    structureChart = new Chart(
      structureCanvas.getContext('2d'),
      {
        type: 'bar',
        options: {
          plugins: {
            legend: {
              display: false
            },
          },
          scales: {
            y: {
              min: 0,
              ticks: {
                stepSize: 1
              }
            }
          }
        },
        data: {
          labels: Object.values(check.content.categories.structure.items).map(row => row.description),
          datasets: [
            {
              label: 'Count',
              data: Object.values(check.content.categories.structure.items).map(row => row.count),
              backgroundColor: '#40E0D0',
            }
          ]
        }
      }
    );
  }

  function initAria() {
    ariaChart = new Chart(
      ariaCanvas.getContext('2d'),
      {
        type: 'bar',
        options: {
          plugins: {
            legend: {
              display: false
            },
          },
          scales: {
            y: {
              min: 0,
              ticks: {
                stepSize: 1
              }
            }
          }
        },
        data: {
          labels: Object.values(check.content.categories.aria.items).map(row => row.description),
          datasets: [
            {
              label: 'Count',
              data: Object.values(check.content.categories.aria.items).map(row => row.count),
              backgroundColor: '#9400D3',
            }
          ]
        }
      }
    );
  }
</script>

<Paper color="secondary" style="width: 100%">
    <Wrapper rich>
        <Title>Details for 
                <span>{check.content.sites[0]}</span>
                <IconButton style="position: relative;">
                    <Icon class="material-icons">info</Icon>
                    <Badge aria-label="unread content count">2</Badge>
                  </IconButton>
                <Tooltip>
                    <Content>
                        <List>
                            {#each check.content.sites as site}
                            <Item>
                                <span>{site}</span>
                            </Item>
                            {/each}
                        </List>
                    </Content>
                </Tooltip>
        </Title>
    </Wrapper>
    <Content>
          <div class="fields-list">
            <div>
                <Textfield disabled value={check.content.title} label="Page Title" contentEditable={false}>
                </Textfield>
            </div>
            <div>
                <Textfield disabled value={date.toLocaleString('en-GB')} label="Time of Analysis">
                </Textfield>
            </div>
            <div>
                <Textfield disabled value={check.content.allitemcount} label="Distinct Items">
                </Textfield>
            </div>
            <div>
                <Textfield disabled value={check.content.totalelements} label="No. of DOM Elements">
                </Textfield>
            </div>
          </div>

          <Accordion multiple style="overflow: auto; overflow-x: hidden; height: 65vh;">
            <Panel extend>
              <Header>
                General Errors
                <span slot="description">Failures to meet minimum accessibility guidelines</span>
              </Header>
              <Content>
                <div class="canvas-container">
                  <div class="panel-canvas"><canvas bind:this={errorCanvas} id="errors"></canvas></div>
                  <div>
                    <p>
                      These errors make users unable to optimally use the page.
                      <a href="https://www.w3.org/WAI/WCAG21/quickref/" target="_blank">
                        <IconButton class="material-icons" size="button">
                        launch
                        </IconButton>
                      </a>
                    </p>
                  </div>
                </div>
              </Content>
            </Panel>
            <Panel extend>
              <Header>
                Contrast Errors
                <span slot="description">Inadequate contrast ratios</span>
              </Header>
              <Content>
                <div class="canvas-container">
                  <div class="panel-canvas"><canvas bind:this={contrastCanvas} id="contrastErrors"></canvas></div>
                  <div>
                    <p>
                      Contrast and color use are vital to accessibility. Users, including users with visual disabilities, must be able to perceive content on the page.
                      <a href="https://www.w3.org/WAI/WCAG21/Understanding/contrast-minimum.html" target="_blank">
                        <IconButton class="material-icons" size="button">
                        launch
                        </IconButton>
                      </a>
                    </p>
                  </div>
                </div>
              </Content>
            </Panel>
            <Panel extend>
              <Header>
                Alerts
                <span slot="description">Noncritical faults and possible improvements</span>
              </Header>
              <Content>
                <div class="canvas-container">
                  <div class="panel-canvas"><canvas bind:this={alertCanvas} id="alertErrors"></canvas></div>
                  <div>
                    <p>
                      These elements can be refined to enhance functionality of accessibility tools.
                      <a href="https://webaim.org/standards/wcag/checklist#sc1.1.1" target="_blank">
                        <IconButton class="material-icons" size="button">
                        launch
                        </IconButton>
                      </a>
                    </p>
                  </div>
                </div>
              </Content>
            </Panel>
            <Panel extend>
              <Header>
                Features
                <span slot="description">Present accessibility features</span>
              </Header>
              <Content>
                <div class="canvas-container">
                  <div class="panel-canvas"><canvas bind:this={featureCanvas} id="featureErrors"></canvas></div>
                  <div>
                    <p>
                      There are features which meet accessibility guidelines, but should be checked for correctness.
                    </p>
                  </div>
                </div>
              </Content>
            </Panel>
            <Panel extend>
              <Header>
                Structural Elements
                <span slot="description">Page architecture for navigation and processing</span>
              </Header>
              <Content>
                <div class="canvas-container">
                  <div class="panel-canvas"><canvas bind:this={structureCanvas} id="structureErrors"></canvas></div>
                  <div>
                    <p>
                      Semantic definitions of content structure for humans and machines alike to infer how the information in the page is located.
                      <a href="https://webaim.org/techniques/semanticstructure/" target="_blank">
                        <IconButton class="material-icons" size="button">
                        launch
                        </IconButton>
                      </a>
                    </p>
                  </div>
                </div>
              </Content>
            </Panel>
            <Panel extend>
              <Header>
                Aria
                <span slot="description">Semantic meaning for content</span>
              </Header>
              <Content>
                <div class="canvas-container">
                  <div class="panel-canvas"><canvas bind:this={ariaCanvas} id="ariaErrors"></canvas></div>
                  <div>
                    <p>
                      The ARIA (Accessible Rich Internet Applications Suite) provides a framework for adding attributes to identify features for user interaction, how they relate to each other, and their current state.
                      <a href="https://www.w3.org/WAI/standards-guidelines/aria/" target="_blank">
                        <IconButton class="material-icons" size="button">
                        launch
                        </IconButton>
                      </a>
                    </p>
                  </div>
                </div>
              </Content>
            </Panel>
          </Accordion>
    </Content>
  </Paper>
  
  <style>
    .fields-list {
        display: flex;
        flex-wrap: wrap;
        flex-direction: row;
        padding: 0.2rem;
        margin-bottom: 0.5rem;
        gap: 1rem;
    }

    .panel-canvas {
      min-width: 650px;
    }

    .canvas-container {
      display: flex;
      flex-direction: row;
      gap: 1rem;
    }
  </style>