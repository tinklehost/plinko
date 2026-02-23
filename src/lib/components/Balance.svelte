<script lang="ts">
  import { balance } from '$lib/stores/game';

  const RESTART_BALANCE = 200;

  function restartGame() {
    balance.set(RESTART_BALANCE);
    localStorage.setItem('plinko_balance', String(RESTART_BALANCE));
  }

  $: balanceFormatted = $balance.toLocaleString('en-US', {
    minimumFractionDigits: 2,
    maximumFractionDigits: 2,
  });
</script>

<div class="flex overflow-hidden rounded-md">
  <div
    class="flex gap-2 bg-slate-900 px-3 py-2 text-sm font-semibold tabular-nums text-white sm:text-base"
  >
    <span class="select-none text-gray-500">$</span>
    <span class="min-w-16 text-right">
      {balanceFormatted}
    </span>
  </div>

  <button
    on:click={restartGame}
    class="bg-blue-600 px-4 py-2 text-sm font-medium text-white transition-colors hover:bg-blue-500 active:bg-blue-700 sm:text-base"
  >
    Restart
  </button>
</div>
