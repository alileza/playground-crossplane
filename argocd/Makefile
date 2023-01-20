init:
	@helm repo add argo https://argoproj.github.io/argo-helm
	@helm repo update

install:
	@helm upgrade --install argocd argo/argo-cd \
		--namespace argocd \
		--create-namespace \
		--set global.image.registry=docker.io \
		--set global.image.repository=argoproj/argocd \
		--set global.image.tag=v2.5.7

get-password:
	@kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo

port-forward:
	@kubectl port-forward svc/argocd-server -n argocd 8080:443