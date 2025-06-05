<script>
	import '@evidence-dev/tailwind/fonts.css';
	import '../app.css';
	import { EvidenceDefaultLayout } from '@evidence-dev/core-components';
	export let data;
</script>

<EvidenceDefaultLayout {data} title="Data Quality" homePageName="KK - FMM" logo="lzs-logo.png" builtWithEvidence=false hideBreadcrumbs=true>
	<slot slot="content" />
</EvidenceDefaultLayout>
