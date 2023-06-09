<script>
	import { enhance } from '$app/forms';
    import Button from '@smui/button/src/Button.svelte';
    import { Label } from '@smui/common';
    import Card, {
        Content,
        PrimaryAction,
        Actions,
        ActionButtons,
        ActionIcons,
    } from '@smui/card';
    import Textfield from '@smui/textfield';
    import HelperText from '@smui/textfield/helper-text';
    import List, { Meta } from '@smui/list';
    import Item from '@smui/list/src/Item.svelte';

    let siteUrl = '';
    let domain = '';
</script>

<form method="POST" action="?/check" use:enhance>
    <div class="main-card">
        <Card variant="outlined" padded>
          <Content>
            <Textfield style="width: 100%;" bind:value={siteUrl} label="URL" required/>
            <Textfield style="width: 100%;" bind:value={domain} label="Domain" required/>
          </Content>
          <Actions fullBleed>
            <Button>
              <Label>Check</Label>
              <i class="material-icons" aria-hidden="true">arrow_forward</i>
            </Button>
          </Actions>
        </Card>
      </div>
</form>

<style>

    .main-card {
        max-width: 22em;
        margin-left: auto;
        margin-right: auto;
    }
</style>

