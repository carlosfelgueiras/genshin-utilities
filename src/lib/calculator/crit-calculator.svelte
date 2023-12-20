<script lang="ts">
	import { FloatingLabelInput, Helper } from 'flowbite-svelte';
	let critRate = 5;
	let critDmg = 50;

	$: state = critRate > 0 && critDmg > 0; // Is valid

	$: critRateDecimal = critRate / 100;
	$: critDmgDecimal = critDmg / 100;
	$: critMultiplier = 1 + critRateDecimal * critDmgDecimal;
	$: critValue = 2 * critRateDecimal + critDmgDecimal;
	$: optimalCritRate = Math.min(1, critValue / 4);
	$: optimalCritDmg = critValue - 2 * optimalCritRate;
	$: optimalCritMultiplier = 1 + optimalCritRate * optimalCritDmg;

	function displayNumber(num: number) {
		return state ? (num * 100).toFixed(2) : undefined;
	}
</script>

<div class="grid grid-cols-1 gap-6">
	<div class="grid gap-6 grid-cols-1 md:grid-cols-2">
		<div>
			<FloatingLabelInput type="number" style="outlined" bind:value={critRate} min="0" step="1">
				Crit Rate
			</FloatingLabelInput>
			<Helper>Your character's Crit Rate, including buffs.</Helper>
		</div>

		<div>
			<FloatingLabelInput style="outlined" value={displayNumber(optimalCritRate)} disabled>
				Optimal Crit Rate
			</FloatingLabelInput>
			<Helper>The value of Crit Rate that maximises your character's average damage.</Helper>
		</div>

		<div>
			<FloatingLabelInput type="number" style="outlined" bind:value={critDmg}>Crit DMG</FloatingLabelInput>
			<Helper>Your character's Crit DMG, including buffs.</Helper>
		</div>

		<div>
			<FloatingLabelInput style="outlined" value={displayNumber(optimalCritDmg)} disabled>
				Optimal Crit DMG
			</FloatingLabelInput>
			<Helper>The value of Crit DMG that maximises your character's average damage.</Helper>
		</div>

		<div>
			<FloatingLabelInput style="outlined" value={displayNumber(critMultiplier)} disabled>
				Crit Multiplier
			</FloatingLabelInput>
			<Helper>The multiplier that represents the average crit contribution to your damage.</Helper>
		</div>

		<div>
			<FloatingLabelInput style="outlined" value={displayNumber(optimalCritMultiplier)} disabled>
				Optimal Crit Multiplier
			</FloatingLabelInput>
			<Helper>
				The multiplier that represents the optimal average crit contribution to your damage.
			</Helper>
		</div>
	</div>

	<div>
		<FloatingLabelInput style="outlined" value={displayNumber(critValue)} disabled>
			Crit Value
		</FloatingLabelInput>
		<Helper>Crit Value represents the ammount of investment.</Helper>
	</div>
</div>
