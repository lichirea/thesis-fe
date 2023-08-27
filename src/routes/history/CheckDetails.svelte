<script lang="ts">
    import Paper, { Title, Content } from '@smui/paper';
    import Accordion, { Panel, Header } from '@smui-extra/accordion';
    import Textfield from '@smui/textfield';

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


    let name = '';
    let email = '';

    export let check;
    let date = new Date(check.time)
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
      
        
      <Accordion>
        <Panel extend color="primary">
          <Header>
            Panel 1
            <span slot="description">Description of panel 1.</span>
          </Header>
          <Content>
            The content for panel 1.
     
            <ul>
              <li>Some</li>
              <li>List</li>
              <li>Items</li>
            </ul>
          </Content>
        </Panel>
        <Panel extend>
          <Header>
            Panel 2
            <span slot="description">Description of panel 2.</span>
          </Header>
          <Content>The content for panel 2.</Content>
        </Panel>
        <Panel extend>
          <Header>
            Panel 3
            <span slot="description">Description of panel 3.</span>
          </Header>
          <Content>
            The content for panel 3.
     
            <ul>
              <li>Some</li>
              <li>More</li>
              <li>List</li>
              <li>Items</li>
              <li>To</li>
              <li>Show</li>
              <li>Big</li>
              <li>Height</li>
            </ul>
          </Content>
        </Panel>
        <Panel extend>
          <Header>
            Panel 4
            <span slot="description">Description of panel 4.</span>
          </Header>
          <Content>The content for panel 4.</Content>
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
  </style>